<template>
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
</template>

<script setup lang="ts">
import arrow from '~/assets/images/arrow.png';

</script>

<style scoped>
.hero-badge {
  font-family: Golos Text;
  font-weight: 400;
  font-size: 18px;
  line-height: 120%;
  letter-spacing: 0%;
  margin-top: 10px;
}

.hero-card {
  width: 90%;
  height: 289px;
  padding: 1.5rem;
  border-radius: 20px;
  position: relative;
  overflow: hidden;
  background: linear-gradient(135deg, #1500FF 0%, #6C5AE0 100%);
  color: #fff;
  /* display: flex; */
  flex-direction: column;
  /* justify-content: space-between; */
}

.hero-cta--projects {
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
  position: relative;  /* add to anchor arrow positioning */
}

.hero-title {
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

.arrow-icon {
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
.arrow-icon img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  transform: rotate(-45deg) scale(0.5);
}
</style>
