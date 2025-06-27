<template>
  <section class="services-block">
  <h2 class="slider-title">Наши услуги</h2>
  <!-- Mobile cards -->
  <div v-if="isMobile" class="services-cards">
    <div v-for="(service, idx) in services" :key="idx" class="service-card">
      <h3>{{ service.title }}</h3>
      <p>{{ service.description }}</p>
    </div>
  </div>
  <Swiper v-else
    :modules="[Navigation, Autoplay]"
    :spaceBetween="24"
    :slidesPerView="'auto'"
    :navigation="{ prevEl: '.services-slider-prev', nextEl: '.services-slider-next' }"
    
    class="services-slider"
  >
    <SwiperSlide v-for="(service, idx) in services" :key="idx">
      <div class="service-card">
        <h3>{{ service.title }}</h3>
        <p>{{ service.description }}</p>
      </div>
    </SwiperSlide>
  </Swiper>
  <div v-if="!isMobile" class="slider-controls">
    <button class="services-slider-prev control-btn">&#10094;</button>
    <button class="services-slider-next control-btn">&#10095;</button>
  </div>
  </section>
</template>

<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import SwiperCore, { Navigation, Autoplay } from 'swiper'
import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/autoplay'
import { ref, onMounted, onBeforeUnmount } from 'vue'

SwiperCore.use([Navigation, Autoplay])

// Detect mobile viewport to switch between slider and card list
const isMobile = ref(false)
const checkMobile = () => {
  if (typeof window !== 'undefined') {
    isMobile.value = window.innerWidth <= 1000
  }
}

onMounted(() => {
  checkMobile()
  if (typeof window !== 'undefined') {
    window.addEventListener('resize', checkMobile)
  }
})

onBeforeUnmount(() => {
  if (typeof window !== 'undefined') {
    window.removeEventListener('resize', checkMobile)
  }
})


const services = [
  { title: 'Landing page', description: 'Лендинги с адаптивным дизайном для всех типов устройств' },
  { title: 'Внедрение BITRIX24', description: 'Оформление интерфейсов под устройства' },
  { title: 'Интернет-магазин', description: 'Удобные интерфейсы с фокусом на мобильную версию' },
  { title: 'Личный кабинет', description: 'Интуитивно понятные личные кабинеты' },
  { title: 'Техническая поддержка', description: 'Лендинги с адаптивным дизайном для всех типов устройств' },
  { title: 'Сайты на WordPress', description: 'Оформление интерфейсов под устройства' },
  { title: 'Проектирование интерфейса', description: 'Удобные интерфейсы с фокусом на мобильную версию' }
]
</script>

<style scoped>
.services-block { margin: 1rem 0; }
.slider-title {
  text-align: left;
  font-size: 2rem;
  margin-bottom: 0;
}

.slider-controls {
  display: flex;
  justify-content: flex-start;
  gap: 0.5rem;
  margin-top: 1rem;
}

.control-btn {
  background: #fff;
  border: 1px solid #e5e5e5;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  font-size: 1.25rem;
  cursor: pointer;
  color: #333;
}

.control-btn:hover {
  background: #f5f5f5;
}

.services-slider {
  width: 100%;
  padding: 0;
}
.services-slider :deep(.swiper-wrapper) {
  align-items: stretch;
}

.services-slider :deep(.swiper-slide) {
  border-radius: 16px; /* Corner/medium radius */
  background-color: #fff;
  overflow: hidden;
  width: 413px;

  height: 400px !important;
}

.service-card {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  background-color: #fff;
  padding: 30px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.service-card h3 {
  font-family: 'Golos Text', sans-serif;
  font-weight: 500;
  font-size: 44px;
  line-height: 100%;
  letter-spacing: 0%;
  background: linear-gradient(108.96deg, #0804A1 -2.15%, #9278FA 61.85%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 0.75rem;
}
.service-card p {
  font-family: 'Golos Text', sans-serif;
  font-weight: 400;
  font-size: 20px;
  line-height: 140%;
  letter-spacing: 0%;
  color: #333;
  margin: 0;
}
.services-cards {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

@media (max-width: 1000px) {
  .services-slider,
  .slider-controls {
    display: none;
  }

  .service-card {
    width: 100%;
    height: auto !important;
    border-radius: 16px;
    overflow: hidden;
  }
}
</style>
