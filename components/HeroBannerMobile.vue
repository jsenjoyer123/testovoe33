<template>
  <section class="hero-mobile">
    <div class="hero-card hero-card--left">
      <p class="hero-badge">digital creative agency</p>
      <h1 class="hero-title">
        СОЗДАНИЕ
        <br />
        И ПРОДВИЖЕНИЕ
        <br />
        САЙТОВ
      </h1>
      <!-- Thumbnails hidden on mobile -->
      <button class="hero-cta hero-cta--projects">
        Наши проекты
        <span class="arrow-icon"><img :src="arrow" alt="arrow" /></span>
      </button>
    </div>
    <div class="hero-card hero-card--right">
      <img src="~/assets/images/mobileflowers.png" alt="" class="hero-flowers">
      <div class="hero-content">
        <div class="hero-price-block">
          <p class="hero-price-label">ваша цена</p>
          <div class="hero-price">320 000 ₽</div>
        </div>
        <button class="hero-cta" @click="emit('open-modal')">
          <span class="arrow-icon"><img :src="arrow" alt="arrow" /></span>
          Заказать
        </button>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import arrow from '~/assets/images/arrow.png';
const emit = defineEmits(['open-modal']);
</script>

<style scoped>
.hero-mobile {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
}

/* Left card */
.hero-card.hero-card--left {
  width: 90%;
  height: 289px;
  padding: 1.5rem;
  border-radius: 20px;
  position: relative;
  overflow: hidden;
  background: linear-gradient(135deg, #1500FF 0%, #6C5AE0 100%);
  color: #fff;
  display: flex;
  flex-direction: column;
}

.hero-card.hero-card--left .hero-badge {
  font-family: Golos Text;
  font-weight: 400;
  font-size: 18px;
  line-height: 120%;
  letter-spacing: 0%;
  margin-top: 10px;
}

.hero-card.hero-card--left .hero-title {
  display: flex;
  flex-direction: column;
  width: 262px;
  height: 144px;
  gap: 20px;
  font-family: 'Golos Text';
  font-weight: 500;
  font-size: 28px;
  line-height: 120%;
  letter-spacing: 0%;
  text-transform: uppercase;
}

.hero-card.hero-card--left .hero-cta--projects {
  font-family: Golos Text;
  font-weight: 600;
  font-size: 16px;
  line-height: 100%;
  letter-spacing: 0%;
  margin-top: -20px;
  width: 87%;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
  height: 44px;
  padding: 0 1rem;
  background: #fff;
  color: #0D08A4;
  border: none;
  border-radius: 9999px;
  cursor: pointer;
  position: relative;
}

.hero-card.hero-card--left .arrow-icon {
  width: 45px;
  height: 45px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  left: 100%;
  top: 50%;
  transform: translateY(-50%);
  border-radius: 50%;
  background: #c5ff00;
  color: #000;
  font-size: 0.875rem;
}

.hero-card.hero-card--left .arrow-icon img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  transform: rotate(-45deg) scale(0.5);
}

/* Right card */
.hero-card.hero-card--right {
  padding: 1.5rem 1.5rem 0.5rem;
  border-radius: 20px;
  position: relative;
  overflow: visible;
  background-image: linear-gradient(rgba(8, 4, 161, 0.8), rgba(8, 4, 161, 0.8)), url('~/assets/images/background.png');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  color: #fff;
  display: flex;
  width: 90%;
  aspect-ratio: 320 / 250;
}

.hero-card.hero-card--right .hero-flowers {
  position: absolute;
  bottom: 0;
  right: 0;
  width: auto;
  height: 125%;
  z-index: 1;
}

.hero-card.hero-card--right .hero-content {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-end;
  height: 100%;
  width: 100%;
}

.hero-card.hero-card--right .hero-price-block {
  margin-bottom: 0;
}

.hero-card.hero-card--right .hero-price-label {
  margin-bottom: 0;
  padding-bottom: 0;
  font-family: 'Golos Text', sans-serif;
  font-weight: 400;
  font-size: 18px;
  line-height: 1.2;
  opacity: 0.9;
}

.hero-card.hero-card--right .hero-price {
  margin-bottom: 0;
  padding-bottom: 0;
  font-size: 2.5rem;
  font-weight: 700;
  margin: 0.5rem 0;
}

.hero-card.hero-card--right .hero-support {
  color: #c5ff00;
  font-size: 1rem;
  line-height: 1.2;
  margin-top: auto;
  padding-bottom: 1rem;
}

.hero-card.hero-card--right .hero-cta {
  position: relative;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.75rem 1.5rem;
  background: #fff;
  color: #000;
  border: none;
  border-radius: 9999px;
  cursor: pointer;
  width: 99%;
  height: 45px;
  margin: 1rem auto 0;
}

.hero-card.hero-card--right .hero-cta .arrow-icon {
  position: absolute;
  left: 1.5rem;
  top: 50%;
  transform: translateY(-50%);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 38px;
  height: 38px;
  border-radius: 50%;
  background: #c5ff00;
  color: #000;
  font-size: 0.875rem;
}

.hero-card.hero-card--right .hero-cta .arrow-icon img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  transform: scale(0.5);
}
</style>
