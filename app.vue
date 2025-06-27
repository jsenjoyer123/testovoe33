<template>
  <Menu @open-modal="onOpenModal" />
  <div class="content-wrapper">
    <div class="mobile-wrapper">
      <div class="desktop-only">
        <HeroBanner @open-modal="onOpenModal" />
      </div>
      <div class="mobile-only">
        <HeroBannerMobile @open-modal="onOpenModal" />
      </div>
    </div>
    <div class="container">
      <ServicesSlider />
      <Calculator @open-modal="onOpenModal" />
    </div>
  </div>
  <Modal v-if="showModal" :message="modalMessage" @close="closeModal" />
</template>

<script setup>
import { ref } from 'vue'
import Menu from '~/components/Menu.vue'
import ServicesSlider from '~/components/ServicesSlider.vue'
import HeroBanner from '~/components/HeroBanner.vue'
import HeroBannerMobile from '~/components/HeroBannerMobile.vue'
import Calculator from '~/components/Calculator.vue'
import Modal from '~/components/Modal.vue'

const showModal = ref(false)
const modalMessage = ref('')

const onOpenModal = (price) => {
  if (price !== undefined) {
    modalMessage.value = `Мы рассчитали стоимость вашего сайта — она составила ${price.toLocaleString()} рублей. Оставьте свои контакты, и наш менеджер свяжется с вами в ближайшее время.`
  } else {
    modalMessage.value = 'Оставьте свои контакты, и наш менеджер свяжется с вами в ближайшее время.'
  }
  showModal.value = true
}

const closeModal = () => {
  showModal.value = false
}
</script>

<style>
html, body, #__nuxt {
  background-color: #F2F2F4;
  margin: 0;
  overflow-x: hidden;
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.desktop-only { display: block; }
.mobile-only { display: none; }

@media (max-width: 1000px) {
  .content-wrapper {
    padding: 0 20px;
  }
}

@media (max-width: 1000px) {
  .desktop-only { display: none; }
  .mobile-only { display: block; }
}
</style>
