<script setup lang="ts">
import { ref, provide } from 'vue'
import Navbar from './components/Navbar.vue'
import HeroSection from './components/HeroSection.vue'
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
    
    <!-- Home Page -->
    <div v-if="currentPage === 'home'">
      <HeroSection @navigate="navigateTo" />
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
</style>
