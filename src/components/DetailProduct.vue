<script setup lang="ts">
import { ref, inject } from 'vue'
import pagarDImg from '../assets/produk/PagarD.png'
import kanopiDImg from '../assets/produk/KanopiD.png'
import kusenAluDImg from '../assets/produk/Kusn_AluD.png'
import garasiD1Img from '../assets/produk/GarasiD1.png'
import garasiD2Img from '../assets/produk/GarasiD2.png'
import tralisDImg from '../assets/produk/TralisD.png'
import tangkiGalvDImg from '../assets/produk/TanGalvD.png'
import whatsappIcon from '../assets/whatsapp.png'

interface ProductDetail {
  id: number
  title: string
  duration: string
  unit: string
  price: string
  image: string
  observationTime: string
  orderTime: string
  material: string
  requiredMaterials: string[]
  notes: string[]
  advantages?: string[]
  disadvantages?: string[]
  priceExample: {
    dimension: string
    price: string
  }
}

const props = defineProps<{
  productId: number
}>()

const navigateTo = inject<(page: string, productId?: number) => void>('navigateTo')

const productDetails: Record<number, ProductDetail> = {
  1: {
    id: 1,
    title: 'Pagar Galvanis',
    duration: '±3-6 hari',
    unit: 'Meter',
    price: 'Rp700.000',
    image: pagarDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Galvanis',
    requiredMaterials: [
      'Besi hollo/ square',
      'Balok Kayu',
      'Besi pejal',
      'Besi Ram',
      'Plat strip',
      'Cat besi'
    ],
    advantages: [
      'Lebih terjangkau',
      'Cukup tahan terhadap korosi ringan'
    ],
    disadvantages: [
      'Kurang ideal untuk investasi jangka panjang',
      'Kurang tangguh di kondisi ekstrem'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran'
    ],
    priceExample: {
      dimension: 'Panjang 5 x Tinggi 2 Meter',
      price: 'Rp7.000.000'
    }
  },
  2: {
    id: 2,
    title: 'Pagar Stainless Steel',
    duration: '±3-6 hari',
    unit: 'Meter',
    price: 'Rp1.300.000',
    image: pagarDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Stainless Steel',
    requiredMaterials: [
      'Besi hollow/square',
      'Balok Kayu',
      'Besi pejal',
      'Besi Ram',
      'Plat strip',
      'Cat besi'
    ],
    advantages: [
      'Elegan dan profesional',
      'Tahan karat dan cuaca ekstrem',
      'Minim perawatan, umur panjang'
    ],
    disadvantages: [
      'Investasi awal lebih tinggi',
      'Membutuhkan teknik pengerjaan khusus'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran'
    ],
    priceExample: {
      dimension: 'Panjang 5 x Tinggi 2 Meter',
      price: 'Rp13.000.000'
    }
  },
  3: {
    id: 3,
    title: 'Kanopi Rangka Baja Ringan',
    duration: '±3-6 hari',
    unit: 'Meter',
    price: 'Rp250.000',
    image: kanopiDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Baja ringan',
    requiredMaterials: [
      'Baja ringan',
      'Atap genteng metal',
      'Atap alderon',
      'Atap spandek'
    ],
    advantages: [
      'Pemasangan cepat dan efisien',
      'Bobot ringan namun tetap kokoh',
      'Tahan terhadap karat dan cuaca ekstrem',
      'Biaya perawatan rendah'
    ],
    disadvantages: [
      'Kurang ideal untuk bentangan sangat lebar tanpa tambahan penopang',
      'Pilihan model dan bentuk sedikit terbatas dibanding material lain'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran'
    ],
    priceExample: {
      dimension: 'Panjang 5 x Lebar 2 Meter',
      price: 'Rp250.000'
    }
  },
  4: {
    id: 4,
    title: 'Kanopi Rangka Hollo',
    duration: '±3-6 hari',
    unit: 'Meter',
    price: 'Rp450.000',
    image: kanopiDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Hollo/square',
    requiredMaterials: [
      'Besi hollo/square',
      'Besi pipa',
      'Atap genteng metal',
      'Atap alderon',
      'Atap spandek'
    ],
    advantages: [
      'Tampilan lebih rapi dan modern',
      'Mudah dibentuk dan dikombinasikan dengan berbagai desain',
      'Pilihan ukuran dan ketebalan lebih beragam',
      'Cocok untuk hunian minimalis hingga komersial'
    ],
    disadvantages: [
      'Rentan berkarat jika tidak dilapisi cat anti karat',
      'Membutuhkan perawatan rutin agar tahan lama'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran'
    ],
    priceExample: {
      dimension: 'Panjang 5 x Lebar 2 Meter',
      price: 'Rp450.000'
    }
  },
  5: {
    id: 5,
    title: 'Kusen Aluminium Pintu',
    duration: '±3-6 hari',
    unit: 'Unit',
    price: 'Rp2.200.000',
    image: kusenAluDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Stainless Steel',
    requiredMaterials: [
      'Besi hollow/square',
      'Balok Kayu',
      'Besi pipa',
      'Besi Ram',
      'Plat strip',
      'Cat besi'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran'
    ],
    priceExample: {
      dimension: 'Panjang 5 x Tinggi 2 Meter',
      price: 'Rp2.200.000'
    }
  },
  6: {
    id: 6,
    title: 'Kusen Aluminium Jendela',
    duration: '±3-6 hari',
    unit: 'Unit',
    price: 'Rp900.000',
    image: kusenAluDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Galvanis',
    requiredMaterials: [
      'Besi hollow/square',
      'Balok Kayu',
      'Besi pipa',
      'Besi Ram',
      'Plat strip',
      'Cat besi'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran'
    ],
    priceExample: {
      dimension: 'Panjang 5 x Tinggi 2 Meter',
      price: 'Rp900.000'
    }
  },
  7: {
    id: 7,
    title: 'Garasi Handerson',
    duration: '±3-6 hari',
    unit: 'Meter',
    price: 'Rp1.200.000',
    image: garasiD1Img,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Stainless Steel',
    requiredMaterials: [
      'Besi hollow/square',
      'Balok Kayu',
      'Besi pipa',
      'Besi Ram',
      'Plat strip',
      'Cat besi'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran'
    ],
    priceExample: {
      dimension: 'Panjang 5 x Tinggi 2 Meter',
      price: 'Rp12.000.000'
    }
  },
  8: {
    id: 8,
    title: 'Folding Gate',
    duration: '±3-6 hari',
    unit: 'Meter',
    price: 'Rp600.000',
    image: garasiD2Img,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Galvanis',
    requiredMaterials: [
      'Besi hollow/square',
      'Balok Kayu',
      'Besi pipa',
      'Besi Ram',
      'Plat strip',
      'Cat besi'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran',
      'Satuan minimum: 7m'
    ],
    priceExample: {
      dimension: 'Panjang 5 x Tinggi 2 Meter',
      price: 'Rp6.000.000'
    }
  },
  9: {
    id: 9,
    title: 'Tralis Jendela',
    duration: '±3-6 hari',
    unit: 'Unit',
    price: 'Rp350.000',
    image: tralisDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Stainless Steel',
    requiredMaterials: [
      'Besi hollow/square',
      'Balok Kayu',
      'Besi pipa',
      'Besi Ram',
      'Plat strip',
      'Cat besi'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran',
      'Jika dimensi lebih besar, harga berbeda',
      'Ukuran standar minimal: Lebar 0,5 x Tinggi 1,5 Meter'
    ],
    priceExample: {
      dimension: 'Lebar 0,5 x Tinggi 1,5 Meter',
      price: 'Rp350.000'
    }
  },
  10: {
    id: 10,
    title: 'Tralis Pintu',
    duration: '±3-6 hari',
    unit: 'Unit',
    price: 'Rp900.000',
    image: tralisDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Galvanis',
    requiredMaterials: [
      'Besi hollow/square',
      'Balok Kayu',
      'Besi pipa',
      'Besi Ram',
      'Plat strip',
      'Cat besi'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran',
      'Jika dimensi lebih besar, harga berbeda',
      'Ukuran standar minimal: Lebar 1 x Tinggi 2 Meter'
    ],
    priceExample: {
      dimension: 'Lebar 1 x Tinggi 2 Meter',
      price: 'Rp900.000'
    }
  },
  11: {
    id: 11,
    title: 'Tangga Galvanis',
    duration: '±3-6 hari',
    unit: 'Meter',
    price: 'Rp1.200.000',
    image: tangkiGalvDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Stainless Steel',
    requiredMaterials: [
      'Besi hollow/square',
      'Balok Kayu',
      'Besi pipa',
      'Besi Ram',
      'Plat strip',
      'Cat besi'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran'
    ],
    priceExample: {
      dimension: 'Panjang 5 x Tinggi 2 Meter',
      price: 'Rp13.000.000'
    }
  }
  ,
  12: {
    id: 12,
    title: 'Atap Baja Ringan',
    duration: '±3-6 hari',
    unit: 'Meter',
    price: 'Rp300.000',
    image: kanopiDImg,
    observationTime: '±3 Jam',
    orderTime: '±1 Hari',
    material: 'Baja ringan',
    requiredMaterials: [
      'Kerangka baja ringan',
      'Atap genteng metal',
      'Atap spandek',
      'Atap genteng press'
    ],
    notes: [
      'Model bisa request',
      'Harga bisa nego saat pengukuran'
    ],
    priceExample: {
      dimension: 'Panjang 10 x Lebar 8 x 1,3',
      price: 'Rp300.000 × (P x L x 1.3)'
    }
  }
}

const currentProduct = ref<ProductDetail>(productDetails[props.productId] ?? productDetails[1]!)

const goBack = () => {
  if (navigateTo) {
    navigateTo('produk')
  }
}

// whatsapp integration
const whatsappNumber = '628988571705'

const buildWhatsAppMessage = (type: 'consult' | 'order') => {
  const p = currentProduct.value
  if (!p) return ''

  if (type === 'consult') {
    return `Halo, saya ingin konsultasi mengenai produk *${p.title}*.\nLama pengerjaan: ${p.duration}.\nPerkiraan harga: ${p.price}.\nMohon informasi lebih lanjut. Terima kasih.`
  }

  // order
  return `Halo, saya ingin memesan produk *${p.title}*.\nLama pengerjaan: ${p.duration}.\nPerkiraan harga: ${p.price}.\nMohon informasikan langkah selanjutnya untuk pemesanan. Terima kasih.`
}

const waHref = (type: 'consult' | 'order') => {
  const msg = buildWhatsAppMessage(type)
  const encoded = encodeURIComponent(msg)
  return `https://wa.me/${whatsappNumber}?text=${encoded}`
}
</script>

<template>
  <section class="detail-page">
    <div class="detail-container">
      <!-- Back Button -->
      <button class="back-btn" @click="goBack">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
          <line x1="19" y1="12" x2="5" y2="12"></line>
          <polyline points="12 19 5 12 12 5"></polyline>
        </svg>
        <span>Kembali ke Produk</span>
      </button>

      <!-- Product Overview -->
      <div class="product-overview">
        <!-- Product Image -->
        <div class="product-image-section">
          <img :src="currentProduct.image" :alt="currentProduct.title" class="product-main-image" />
        </div>

        <!-- Product Header -->
        <div class="product-header">
          <h2 class="product-title">{{ currentProduct.title }}</h2>
          <div class="product-meta">
            <div class="meta-item">
              <span class="meta-label">Lama Pengerjaan:</span>
              <span class="meta-value">{{ currentProduct.duration }}</span>
            </div>
            <div class="meta-item">
              <span class="meta-label">Satuan:</span>
              <span class="meta-value">{{ currentProduct.unit }}</span>
            </div>
          </div>
          <div class="product-price">{{ currentProduct.price }}/{{ currentProduct.unit }}</div>
        </div>
      </div>

      <!-- Detail Section -->
      <div class="detail-section">
        <h3 class="section-title">Detail:</h3>
        
        <div class="detail-item">
          <span class="detail-label">Lama observasi tempat:</span>
          <span class="detail-value">{{ currentProduct.observationTime }}</span>
        </div>

        <div class="detail-item">
          <span class="detail-label">Lama Pemesanan Bahan:</span>
          <span class="detail-value">{{ currentProduct.orderTime }}</span>
        </div>

        <div class="detail-item">
          <span class="detail-value">Berbahan dasar {{ currentProduct.material }}</span>
        </div>

        <div class="materials-section">
          <h4 class="subsection-title">Contoh bahan yang di butuhkan:</h4>
          <ul class="materials-list">
            <li v-for="(material, index) in currentProduct.requiredMaterials" :key="index">
              {{ material }}
            </li>
          </ul>
          <p class="materials-note">*Bahan menyesuaikan dengan kebutuhan</p>
        </div>

        <div class="notes-section">
          <h4 class="subsection-title">Note:</h4>
          <ul class="notes-list">
            <li v-for="(note, index) in currentProduct.notes" :key="index">
              {{ note }}
            </li>
          </ul>
        </div>

        <!-- Advantages (Kelebihan) -->
        <div v-if="currentProduct.advantages && currentProduct.advantages.length" class="advantages-section">
          <h4 class="subsection-title">Kelebihan:</h4>
          <ul class="notes-list">
            <li v-for="(item, i) in currentProduct.advantages" :key="'adv-'+i">{{ item }}</li>
          </ul>
        </div>

        <!-- Disadvantages (Kekurangan) -->
        <div v-if="currentProduct.disadvantages && currentProduct.disadvantages.length" class="disadvantages-section">
          <h4 class="subsection-title">Kekurangan:</h4>
          <ul class="notes-list">
            <li v-for="(item, i) in currentProduct.disadvantages" :key="'dis-'+i">{{ item }}</li>
          </ul>
        </div>

        <div class="price-example">
          <h4 class="subsection-title">Prediksi harga di {{ currentProduct.priceExample.dimension }}</h4>
          <div class="example-price">= {{ currentProduct.priceExample.price }}</div>
          <p v-if="currentProduct.priceExample && currentProduct.priceExample.dimension.includes('1,3')" class="slope-note">*1,3 adalah rumus kemiringan/sudut</p>
        </div>
      </div>

      <!-- Action Buttons (open WhatsApp with prefilled message) -->
      <div class="action-buttons">
        <a :href="waHref('consult')" target="_blank" rel="noopener noreferrer" class="btn-consultation">
          <img :src="whatsappIcon" alt="WhatsApp" class="btn-icon" />
          Konsultasi Gratis
        </a>
        <a :href="waHref('order')" target="_blank" rel="noopener noreferrer" class="btn-order">
          <img :src="whatsappIcon" alt="WhatsApp" class="btn-icon" />
          Pesan Sekarang
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.detail-page {
  min-height: 100vh;
  padding: 120px 2rem 4rem;
  background: #f8fafc;
}

.detail-container {
  max-width: 1200px;
  margin: 0 auto;
  background: #ffffff;
  border-radius: 16px;
  padding: 3rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

.back-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: #f1f5f9;
  border: 2px solid #e5e7eb;
  padding: 0.75rem 1.5rem;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease;
  color: #64748b;
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 2rem;
}

.back-btn:hover {
  background: #1e3a8a;
  color: #ffffff;
  border-color: #1e3a8a;
  transform: translateX(-5px);
}

.product-overview {
  display: flex;
  gap: 2rem;
  margin-bottom: 2rem;
  padding-bottom: 2rem;
  border-bottom: 2px solid #e5e7eb;
}

.product-image-section {
  flex-shrink: 0;
  width: 350px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.product-main-image {
  width: 100%;
  height: 300px;
  object-fit: cover;
  display: block;
}

.product-header {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.product-title {
  font-size: 2rem;
  font-weight: 800;
  color: #1e3a8a;
  margin-bottom: 1rem;
}

.product-meta {
  display: flex;
  gap: 2rem;
  margin-bottom: 1rem;
  flex-wrap: wrap;
}

.meta-item {
  display: flex;
  gap: 0.5rem;
}

.meta-label {
  font-size: 1rem;
  color: #666;
  font-weight: 500;
}

.meta-value {
  font-size: 1rem;
  color: #2c3e50;
  font-weight: 600;
}

.product-price {
  font-size: 1.75rem;
  font-weight: 800;
  color: #1e3a8a;
  margin-top: 1rem;
}

.detail-section {
  margin-bottom: 2rem;
}

.section-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: #2c3e50;
  margin-bottom: 1.5rem;
}

.detail-item {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1rem;
  line-height: 1.6;
}

.detail-label {
  font-size: 1rem;
  color: #666;
  font-weight: 500;
}

.detail-value {
  font-size: 1rem;
  color: #2c3e50;
  font-weight: 600;
}

.materials-section,
.notes-section {
  margin: 1.5rem 0;
  padding: 1.5rem;
  background: #f8fafc;
  border-radius: 12px;
}

.subsection-title {
  font-size: 1.1rem;
  font-weight: 700;
  color: #2c3e50;
  margin-bottom: 1rem;
}

.materials-list,
.notes-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.advantages-section,
.disadvantages-section {
  margin: 1.5rem 0;
  padding: 1.5rem;
  background: #fff7ed;
  border-radius: 12px;
  border: 1px solid #f59e0b33;
}

.disadvantages-section {
  background: #fff1f2;
  border: 1px solid #ef444433;
}

.materials-list li,
.notes-list li {
  padding-left: 1.5rem;
  position: relative;
  margin-bottom: 0.75rem;
  color: #2c3e50;
  font-size: 1rem;
  line-height: 1.6;
}

.materials-list li::before {
  content: "•";
  position: absolute;
  left: 0;
  color: #1e3a8a;
  font-weight: 800;
  font-size: 1.2rem;
}

.notes-list li::before {
  content: "✓";
  position: absolute;
  left: 0;
  color: #10b981;
  font-weight: 800;
  font-size: 1rem;
}

.materials-note {
  margin-top: 1rem;
  font-size: 0.9rem;
  color: #dc2626;
  font-style: italic;
  font-weight: 600;
}

.price-example {
  margin-top: 2rem;
  padding: 1.5rem;
  background: #f0f9ff;
  border: 2px solid #1e3a8a;
  border-radius: 12px;
}

.price-example .subsection-title {
  color: #1e3a8a;
  margin-bottom: 0.75rem;
}

.example-price {
  font-size: 1.75rem;
  font-weight: 800;
  color: #1e3a8a;
  margin-top: 0.5rem;
}

.slope-note {
  margin-top: 0.5rem;
  font-size: 0.95rem;
  color: #334155;
  font-style: italic;
}

.action-buttons {
  display: flex;
  gap: 1rem;
  margin-top: 2rem;
  flex-wrap: wrap;
}

.btn-consultation,
.btn-order {
  flex: 1;
  min-width: 200px;
  padding: 1rem 2rem;
  border: none;
  border-radius: 50px;
  font-size: 1.1rem;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

.btn-icon {
  width: 24px;
  height: 24px;
  object-fit: contain;
}

.btn-consultation {
  background: #ffffff;
  color: #1e3a8a;
  border: 2px solid #1e3a8a;
}

.btn-consultation:hover {
  background: #f0f9ff;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(30, 58, 138, 0.2);
}

.btn-order {
  background: #1e3a8a;
  color: #ffffff;
}

.btn-order:hover {
  background: #1e40af;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(30, 58, 138, 0.4);
}

/* Responsive */
@media (max-width: 768px) {
  .detail-container {
    padding: 2rem 1.5rem;
  }

  .product-overview {
    flex-direction: column;
    gap: 1.5rem;
  }

  .product-image-section {
    width: 100%;
  }

  .product-main-image {
    height: 250px;
  }

  .product-title {
    font-size: 1.5rem;
  }

  .product-price {
    font-size: 1.5rem;
  }

  .product-meta {
    flex-direction: column;
    gap: 0.75rem;
  }

  .action-buttons {
    flex-direction: column;
  }

  .btn-consultation,
  .btn-order {
    min-width: 100%;
  }

  .example-price {
    font-size: 1.5rem;
  }
}

@media (max-width: 480px) {
  .detail-container {
    padding: 1.5rem 1rem;
  }

  .product-title {
    font-size: 1.25rem;
  }

  .section-title {
    font-size: 1.25rem;
  }
}
</style>