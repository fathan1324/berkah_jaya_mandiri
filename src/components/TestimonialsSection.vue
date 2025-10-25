<script setup lang="ts">
import { ref } from 'vue'

import product1Img from '../assets/testi/custmr1.png'
import product2Img from '../assets/testi/custmr2.png'
import product3Img from '../assets/testi/custmr3.png'

interface Testimonial {
  id: number
  name: string
  image: string
  text: string
  rating: number
}

const testimonials = ref<Testimonial[]>([
  {
    id: 1,
    name: 'Pak Hendri',
    image: product1Img,
    text: 'Saya puas dengan hasilnya',
    rating: 5
  },
  {
    id: 2,
    name: 'Koh Aliong',
    image: product2Img,
    text: 'Surprisingly, dapat diandalkan untuk tim yang terbatas',
    rating: 5
  },
  {
    id: 3,
    name: 'Ahmad Wijaya',
    image: product3Img,
    text: 'Harganya bersaing',
    rating: 5
  }
])
</script>

<template>
  <section class="testimonials-section">
    <div class="testimonials-container">
      <div class="section-header">
        <h2 class="section-title">Testimoni Pelanggan</h2>
        <p class="section-subtitle">
          Kepuasan pelanggan adalah prioritas utama kami
        </p>
      </div>

      <div class="testimonials-grid">
        <div 
          v-for="testimonial in testimonials" 
          :key="testimonial.id" 
          class="testimonial-card"
        >
          <div class="product-image-wrapper">
            <img 
              :src="testimonial.image" 
              :alt="`Hasil produk untuk ${testimonial.name}`" 
              class="product-image"
            />
          </div>
          
          <div class="testimonial-content">
            <div class="rating">
              <span v-for="star in testimonial.rating" :key="star" class="star">⭐</span>
            </div>
            
            <p class="testimonial-text">"{{ testimonial.text }}"</p>
            
            <div class="customer-info">
              <h3 class="customer-name">{{ testimonial.name }}</h3>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.testimonials-section {
  padding: 5rem 2rem;
  background: #ffffff;
}

.testimonials-container {
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
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

.testimonial-card {
  background: #ffffff;
  border: 2px solid #e5e7eb;
  border-radius: 16px;
  overflow: hidden;
  transition: all 0.3s ease;
}

.testimonial-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
  border-color: #1e3a8a;
}

.product-image-wrapper {
  width: 100%;
  height: 250px;
  overflow: hidden;
  background-color: #f0f0f0;
}

.product-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.testimonial-card:hover .product-image {
  transform: scale(1.05);
}

.testimonial-content {
  padding: 2rem;
}

.rating {
  margin-bottom: 1rem;
  font-size: 1.2rem;
}

.star {
  margin-right: 0.1rem;
}

.testimonial-text {
  font-size: 1rem;
  line-height: 1.7;
  color: #555;
  font-style: italic;
  margin-bottom: 1.5rem;
}

.customer-info {
  padding-top: 1rem;
  border-top: 2px solid #e5e7eb;
}

.customer-name {
  font-size: 1.1rem;
  font-weight: 700;
  color: #2c3e50;
  margin: 0;
}

/* Responsive */
@media (max-width: 768px) {
  .testimonials-section {
    padding: 3rem 1rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .section-subtitle {
    font-size: 1rem;
  }

  .testimonials-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .product-image-wrapper {
    height: 200px;
  }

  .testimonial-content {
    padding: 1.5rem;
  }

  .customer-name {
    font-size: 1.05rem;
  }

  .testimonial-text {
    font-size: 0.95rem;
  }
}
</style>
