<script setup lang="ts">
import { ref, provide } from 'vue'
import Navbar from './components/Navbar.vue'
import ServicesSection from './components/ServicesSection.vue'
import TestimonialsSection from './components/TestimonialsSection.vue'
import ProductsPage from './components/ProductsPage.vue'
import DetailProduct from './components/DetailProduct.vue'

const currentPage = ref<string>('home')
const selectedProductId = ref<number>(1)

const navigateTo = (page: string, productId?: number) => {
  currentPage.value = page
  if (productId !== undefined) {
    selectedProductId.value = productId
  }
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

provide('navigateTo', navigateTo)
</script>

<template>
  <div class="app">
    <Navbar :current-page="currentPage" @navigate="navigateTo" />
    
    <!-- Home Page (E-Katalog) -->
    <div v-if="currentPage === 'home'">
      <section class="catalog-hero">
        <div class="catalog-hero-container">
          <h1 class="catalog-title">E-Katalog Jasa Las</h1>
          <p class="catalog-subtitle">Temukan layanan & produk kami — pagar, kanopi, kusen, tralis, pintu garasi, dan lainnya. Pilih kategori atau lihat detail untuk informasi lengkap dan pemesanan.</p>
        </div>
      </section>

      <ServicesSection />

      <TestimonialsSection />
    </div>
    
    <!-- Products Page -->
    <ProductsPage v-else-if="currentPage === 'produk'" />
    
    <!-- Detail Product Page -->
    <DetailProduct v-else-if="currentPage === 'detail'" :product-id="selectedProductId" />
  </div>
</template>

<style scoped>
.app {
  width: 100%;
  min-height: 100vh;
}

.catalog-hero {
  padding: 6rem 2rem 2rem;
  background: linear-gradient(90deg, #f8fafc 0%, #eef2ff 100%);
  text-align: center;
}

.catalog-hero-container {
  max-width: 1100px;
  margin: 0 auto;
}

.catalog-title {
  font-size: 3.5rem;
  color: #0f172a;
  font-weight: 800;
  margin-bottom: 0.75rem;
}

.catalog-subtitle {
  color: #334155;
  max-width: 900px;
  margin: 0 auto;
  font-size: 1.05rem;
}

.catalog-actions .catalog-cta {
  background: #1e3a8a;
  color: #fff;
  border: none;
  padding: 0.85rem 1.5rem;
  border-radius: 999px;
  font-weight: 700;
  cursor: pointer;
}

.catalog-actions .catalog-cta:hover {
  background: #1e40af;
}
</style>
