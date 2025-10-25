<script setup lang="ts">
import { ref } from 'vue'

import garasiImg from '../assets/jasa/Garasi.png'
import kanopiImg from '../assets/jasa/Kanopi.png'
import kusenAluImg from '../assets/jasa/Kusn_Alu.png'
import pagarImg from '../assets/jasa/Pgar.png'
import tangkiGalvanisImg from '../assets/jasa/TanGalvans.png'
import tralisImg from '../assets/jasa/Tralis.png'

interface Service {
  id: number
  title: string
  image: string
}

const services = ref<Service[]>([
  {
    id: 1,
    title: 'Pagar Besi',
    image: pagarImg
  },
  {
    id: 2,
    title: 'Kanopi',
    image: kanopiImg
  },
  {
    id: 3,
    title: 'Tralis Jendela',
    image: tralisImg
  },
  {
    id: 4,
    title: 'Pintu Garasi',
    image: garasiImg
  },
  {
    id: 5,
    title: 'Kusen Aluminium',
    image: kusenAluImg
  },
  {
    id: 6,
    title: 'Tangki Galvanis',
    image: tangkiGalvanisImg
  }
])
</script>

<template>
  <section id="produk" class="services-section">
    <div class="services-container">
      <div class="section-header">
        <h2 class="section-title">Layanan Kami</h2>
        <p class="section-subtitle">
          Kami menyediakan berbagai layanan jasa las
        </p>
      </div>

      <div class="services-grid">
        <div 
          v-for="service in services" 
          :key="service.id" 
          class="service-card"
        >
          <img 
            :src="service.image" 
            :alt="service.title" 
            class="service-image"
          />
          <div class="service-overlay"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services-section {
  padding: 5rem 2rem;
  background: #f8fafc;
}

.services-container {
  max-width: 1200px;
  margin: 0 auto;
}

.section-header {
  text-align: center;
  margin-bottom: 3rem;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 800;
  color: #2c3e50;
  margin-bottom: 1rem;
  position: relative;
  display: inline-block;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 80px;
  height: 4px;
  background: #1e3a8a;
  border-radius: 2px;
}

.section-subtitle {
  font-size: 1.1rem;
  color: #666;
  margin-top: 1.5rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
}

.service-card {
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  cursor: pointer;
}

.service-image {
  width: 100%;
  height: auto;
  display: block;
  transition: transform 0.3s ease;
}

.service-card:hover .service-image {
  transform: scale(1.05);
}

.service-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.3);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.service-card:hover .service-overlay {
  opacity: 1;
}

/* Responsive */
@media (max-width: 1024px) {
  .services-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .services-section {
    padding: 3rem 1rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .section-subtitle {
    font-size: 1rem;
  }

  .services-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }
}

@media (max-width: 480px) {
  .services-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }
}
</style>
