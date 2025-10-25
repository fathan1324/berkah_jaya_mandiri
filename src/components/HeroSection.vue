<script setup lang="ts">
import logoImage from '../assets/logo.png'

const emit = defineEmits<{
  navigate: [page: string]
}>()

const navigateToProducts = (event: Event) => {
  event.preventDefault()
  emit('navigate', 'produk')
}
</script>

<template>
  <section id="home" class="hero-section">
    <div class="hero-container">
      <div class="hero-content">
        <div class="hero-logo">
          <img :src="logoImage" alt="Berkah Jaya Mandiri Logo" class="hero-logo-img" />
        </div>
        <h1 class="hero-title">Berkah Jaya Mandiri</h1>
        <p class="hero-subtitle">Solusi Terpercaya untuk Kebutuhan Jasa Las Anda</p>
        <p class="hero-description">
          Kami adalah perusahaan jasa las yang berpengalaman dalam menangani berbagai proyek fabrikasi logam, 
          konstruksi baja, dan perbaikan dengan standar kualitas tinggi dan tenaga ahli.
        </p>
        <div class="hero-buttons">
          <a href="#produk" class="btn btn-primary" @click="navigateToProducts">Lihat Produk Kami</a>
          <a href="#tentang" class="btn btn-secondary">Tentang Kami</a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-section {
  min-height: 100vh;
  background: #1e3a8a;
  padding: 120px 2rem 4rem;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.hero-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('data:image/svg+xml,<svg width="60" height="60" viewBox="0 0 60 60" xmlns="http://www.w3.org/2000/svg"><g fill="none" fill-rule="evenodd"><g fill="%23ffffff" fill-opacity="0.05"><path d="M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z"/></g></g></svg>');
  opacity: 0.3;
}

.hero-container {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.hero-content {
  text-align: center;
  color: #ffffff;
  margin-bottom: 4rem;
}

.hero-logo {
  display: flex;
  justify-content: center;
  margin-bottom: 2rem;
}

.hero-logo-img {
  height: 120px;
  width: auto;
  object-fit: contain;
  filter: drop-shadow(0 4px 20px rgba(0, 0, 0, 0.2));
  background-color: rgba(255, 255, 255, 0.9);
  padding: 1rem;
  border-radius: 20px;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 800;
  margin-bottom: 1rem;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
  line-height: 1.2;
}

.hero-subtitle {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  opacity: 0.95;
}

.hero-description {
  font-size: 1.1rem;
  max-width: 800px;
  margin: 0 auto 2.5rem;
  line-height: 1.8;
  opacity: 0.9;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.btn {
  padding: 1rem 2.5rem;
  font-size: 1.1rem;
  font-weight: 600;
  border-radius: 50px;
  text-decoration: none;
  transition: all 0.3s ease;
  display: inline-block;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.btn-primary {
  background-color: #ffffff;
  color: #1e3a8a;
}

.btn-primary:hover {
  background-color: #f0f0f0;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
}

.btn-secondary {
  background-color: transparent;
  color: #ffffff;
  border: 2px solid #ffffff;
}

.btn-secondary:hover {
  background-color: rgba(255, 255, 255, 0.1);
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
}

/* Responsive */
@media (max-width: 768px) {
  .hero-section {
    padding: 100px 1rem 3rem;
  }

  .hero-title {
    font-size: 2.5rem;
  }

  .hero-subtitle {
    font-size: 1.2rem;
  }

  .hero-description {
    font-size: 1rem;
  }

  .hero-logo-img {
    height: 90px;
  }

  .btn {
    padding: 0.9rem 2rem;
    font-size: 1rem;
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: 2rem;
  }

  .hero-subtitle {
    font-size: 1.1rem;
  }

  .hero-description {
    font-size: 0.95rem;
  }

  .hero-logo-img {
    height: 70px;
  }
}
</style>
