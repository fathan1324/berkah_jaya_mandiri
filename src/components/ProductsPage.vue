<script setup lang="ts">
import { ref, computed, inject } from 'vue'

import pagarDImg from '../assets/produk/PagarD.png'
import kanopiDImg from '../assets/produk/KanopiD.png'
import kusenAluDImg from '../assets/produk/Kusn_AluD.png'
import garasiD1Img from '../assets/produk/GarasiD1.png'
import garasiD2Img from '../assets/produk/GarasiD2.png'
import tralisDImg from '../assets/produk/TralisD.png'
import tangkiGalvDImg from '../assets/produk/TanGalvD.png'

interface Product {
  id: number
  title: string
  category: string
  image: string
  price: string
  duration: string
  unit: string
  minOrder?: string
}

const products = ref<Product[]>([
  {
    id: 1,
    title: 'Pagar Galvanis',
    category: 'Pagar',
    image: pagarDImg,
    price: 'Rp 700.000',
    duration: '±3-6 hari',
    unit: 'per meter',
  },
  {
    id: 2,
    title: 'Pagar Stainless Steel',
    category: 'Pagar',
    image: pagarDImg,
    price: 'Rp 1.300.000',
    duration: '±3-6 hari',
    unit: 'per meter'
  },
  {
    id: 3,
    title: 'Kanopi Rangka Baja Ringan',
    category: 'Kanopi',
    image: kanopiDImg,
    price: 'Rp 250.000',
    duration: '2-4 hari',
    unit: 'per meter'
  },
  {
    id: 4,
    title: 'Kanopi Rangka Hollo',
    category: 'Kanopi',
    image: kanopiDImg,
    price: 'Rp 450.000',
    duration: '2-4 hari',
    unit: 'per meter'
  },
  {
    id: 5,
    title: 'Kusen Aluminium Pintu',
    category: 'Kusen',
    image: kusenAluDImg,
    price: 'Rp 2.200.000',
    duration: '±3-6 hari',
    unit: 'per pintu'
  },
  {
    id: 6,
    title: 'Kusen Aluminium Jendela',
    category: 'Kusen',
    image: kusenAluDImg,
    price: 'Rp 900.000',
    duration: '±3-6 hari',
    unit: 'per jendela'
  },
  {
    id: 7,
    title: 'Garasi Handerson',
    category: 'Pintu',
    image: garasiD1Img,
    price: 'Rp 1.200.000',
    duration: '±3-6 hari',
    unit: 'per meter'
  },
  {
    id: 8,
    title: 'Folding Gate',
    category: 'Pintu',
    image: garasiD2Img,
    price: 'Rp 600.000',
    duration: '±3-6 hari',
    unit: 'per meter',
    minOrder: 'minimal 7 meter'
  },
  {
    id: 9,
    title: 'Tralis Jendela',
    category: 'Tralis',
    image: tralisDImg,
    price: 'Rp 350.000',
    duration: '±3-6 hari',
    unit: 'per jendela'
  },
  {
    id: 10,
    title: 'Tralis Pintu',
    category: 'Tralis',
    image: tralisDImg,
    price: 'Rp 900.000',
    duration: '±3-6 hari',
    unit: 'per pintu'
  },
  {
    id: 11,
    title: 'Tangga Galvanis',
    category: 'Tangga',
    image: tangkiGalvDImg,
    price: 'Rp 1.200.000',
    duration: '±3-6 hari',
    unit: 'per meter'
  }
  ,
  {
    id: 12,
    title: 'Atap Baja Ringan',
    category: 'Atap Rumah',
    image: kanopiDImg,
    price: 'Rp 300.000',
    duration: '±3-6 hari',
    unit: 'per meter'
  }
])

const selectedCategory = ref<string>('Semua')
const categories = ref<string[]>(['Semua', 'Pagar', 'Kanopi', 'Kusen', 'Pintu', 'Tralis', 'Tangga', 'Atap Rumah'])
const navigateTo = inject<(page: string, productId?: number) => void>('navigateTo')

const filteredProducts = computed(() => {
  if (selectedCategory.value === 'Semua') {
    return products.value
  }
  return products.value.filter(product => product.category === selectedCategory.value)
})

const openDetail = (productId: number) => {
  if (navigateTo) {
    navigateTo('detail', productId)
  }
}
</script>

<template>
  <section class="products-page">
    <div class="products-container">
      <!-- Header -->
      <div class="page-header">
        <h1 class="page-title">Produk Kami</h1>
        <p class="page-subtitle">
          Berbagai produk berkualitas tinggi untuk kebutuhan konstruksi dan fabrikasi logam Anda
        </p>
      </div>

      <!-- Category Filter -->
      <div class="category-filter">
        <button
          v-for="category in categories"
          :key="category"
          :class="['filter-btn', { active: selectedCategory === category }]"
          @click="selectedCategory = category"
        >
          {{ category }}
        </button>
      </div>

      <!-- Products Grid -->
      <div class="products-grid">
        <div
          v-for="product in filteredProducts"
          :key="product.id"
          class="product-card"
        >
          <div class="product-image-wrapper">
            <img
              :src="product.image"
              :alt="product.title"
              class="product-image"
            />
          </div>
          
          <div class="product-content">
            <h3 class="product-title">{{ product.title }}</h3>
            
            <div class="product-info">
              <div class="info-item">
                <span class="info-label">Harga:</span>
                <span class="info-value price">{{ product.price }}</span>
                <span class="info-unit">{{ product.unit }}</span>
              </div>
              
              <div class="info-item">
                <span class="info-label">Estimasi:</span>
                <span class="info-value">{{ product.duration }}</span>
              </div>
            </div>
            
            <button class="detail-btn" @click="openDetail(product.id)">Lihat Detail</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.products-page {
  min-height: 100vh;
  padding: 120px 2rem 4rem;
  background: #f8fafc;
}

.products-container {
  max-width: 1400px;
  margin: 0 auto;
}

.page-header {
  text-align: center;
  margin-bottom: 3rem;
}

.page-title {
  font-size: 3rem;
  font-weight: 800;
  color: #2c3e50;
  margin-bottom: 1rem;
}

.page-subtitle {
  font-size: 1.2rem;
  color: #666;
  max-width: 800px;
  margin: 0 auto;
}

.category-filter {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
  flex-wrap: wrap;
}

.filter-btn {
  padding: 0.75rem 1.5rem;
  border: 2px solid #e5e7eb;
  background: #ffffff;
  color: #555;
  border-radius: 50px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.filter-btn:hover {
  border-color: #1e3a8a;
  color: #1e3a8a;
}

.filter-btn.active {
  background: #1e3a8a;
  color: #ffffff;
  border-color: #1e3a8a;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.5rem;
}

.product-card {
  background: #ffffff;
  border: 2px solid #e5e7eb;
  border-radius: 12px;
  transition: all 0.3s ease;
  overflow: hidden;
}

.product-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
  border-color: #1e3a8a;
}

.product-image-wrapper {
  width: 100%;
  height: 250px;
  overflow: hidden;
  background: #f1f5f9;
}

.product-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.product-card:hover .product-image {
  transform: scale(1.05);
}

.product-content {
  padding: 1.5rem;
}

.product-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: #2c3e50;
  margin-bottom: 1.25rem;
  line-height: 1.3;
}

.product-info {
  margin-bottom: 1.5rem;
}

.info-item {
  display: flex;
  align-items: baseline;
  margin-bottom: 0.75rem;
  gap: 0.5rem;
}

.info-label {
  font-size: 0.9rem;
  color: #666;
  font-weight: 500;
  min-width: 75px;
}

.info-value {
  font-size: 1rem;
  color: #2c3e50;
  font-weight: 600;
}

.info-value.price {
  color: #1e3a8a;
  font-size: 1.1rem;
  font-weight: 700;
}

.info-unit {
  font-size: 0.85rem;
  color: #666;
  font-style: italic;
}

.info-item.min-order {
  margin-top: 0.5rem;
  padding-top: 0.75rem;
  border-top: 1px solid #e5e7eb;
}

.info-note {
  font-size: 0.85rem;
  color: #dc2626;
  font-weight: 600;
  font-style: italic;
}

.detail-btn {
  width: 100%;
  padding: 0.75rem 1.5rem;
  background: #1e3a8a;
  color: #ffffff;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.detail-btn:hover {
  background: #1e40af;
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(30, 58, 138, 0.4);
}

/* Responsive */
@media (max-width: 1024px) {
  .products-grid {
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  }
}

@media (max-width: 768px) {
  .products-page {
    padding: 100px 1rem 3rem;
  }

  .page-title {
    font-size: 2.5rem;
  }

  .page-subtitle {
    font-size: 1rem;
  }

  .products-grid {
    grid-template-columns: 1fr;
    gap: 1.25rem;
  }

  .category-filter {
    gap: 0.5rem;
  }

  .filter-btn {
    padding: 0.6rem 1.2rem;
    font-size: 0.9rem;
  }

  .product-title {
    font-size: 1.1rem;
  }

  .info-value.price {
    font-size: 1rem;
  }
}
</style>
