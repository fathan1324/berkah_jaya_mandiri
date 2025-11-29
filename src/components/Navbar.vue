<script setup lang="ts">
import { ref, watch } from 'vue'
import logoImage from '../assets/logo.png'

interface Props {
  currentPage?: string
}

const props = defineProps<Props>()
const emit = defineEmits<{
  navigate: [page: string]
}>()

const activeMenu = ref('home')

watch(() => props.currentPage, (newPage) => {
  if (newPage) {
    activeMenu.value = newPage
  }
})

const handleNavigation = (page: string, event: Event) => {
  event.preventDefault()
  activeMenu.value = page
  emit('navigate', page)
}
</script>

<template>
  <nav class="navbar">
    <div class="navbar-container">
      <!-- Logo -->
      <div class="navbar-logo" @click="handleNavigation('home', $event)" style="cursor: pointer;">
        <img :src="logoImage" alt="Berkah Jaya Mandiri Logo" class="logo-img" />
        <span class="company-name">Berkah Jaya Mandiri</span>
      </div>

      <!-- Menu navigasi -->
      <ul class="navbar-menu">
        <li>
          <a 
            href="#home" 
            :class="{ active: activeMenu === 'home' }"
            @click="handleNavigation('home', $event)"
          >
            Home
          </a>
        </li>
        <li>
          <a 
            href="#produk" 
            :class="{ active: activeMenu === 'produk' }"
            @click="handleNavigation('produk', $event)"
          >
            Produk
          </a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background-color: #ffffff;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  z-index: 1000;
  padding: 1rem 0;
}

.navbar-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navbar-logo {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.logo-img {
  height: 50px;
  width: auto;
  object-fit: contain;
}

.company-name {
  font-size: 1.2rem;
  font-weight: 700;
  color: #2c3e50;
  white-space: nowrap;
}

.navbar-menu {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
}

.navbar-menu li a {
  color: #555;
  font-weight: 500;
  font-size: 1rem;
  text-decoration: none;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  transition: all 0.3s ease;
  position: relative;
}

.navbar-menu li a:hover {
  color: #1e3a8a;
  background-color: #dbeafe;
}

.navbar-menu li a.active {
  color: #1e3a8a;
  font-weight: 600;
}

.navbar-menu li a.active::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 1rem;
  right: 1rem;
  height: 2px;
  background-color: #1e3a8a;
}

/* Responsive */
@media (max-width: 768px) {
  .navbar-container {
    padding: 0 1rem;
  }

  .company-name {
    font-size: 1rem;
  }

  .navbar-menu {
    gap: 1rem;
  }

  .navbar-menu li a {
    font-size: 0.9rem;
    padding: 0.4rem 0.8rem;
  }

  .logo-img {
    height: 40px;
  }
}

@media (max-width: 480px) {
  .company-name {
    display: none;
  }

  .navbar-menu {
    gap: 0.5rem;
  }

  .navbar-menu li a {
    font-size: 0.85rem;
    padding: 0.3rem 0.6rem;
  }
}
</style>
