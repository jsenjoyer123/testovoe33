<template>
  <div class="hero-card hero-card--right">
    <p class="hero-support">техподдержка сайта<br />на 30 дней — в подарок</p>
    <img :src="flowerImage" alt="flower" class="hero-image" />
    <p class="hero-price-label">ваша цена</p>
    <div class="hero-price">320 000 ₽</div>
    <button class="hero-cta" @click="emit('open-modal')">
      <span class="arrow-icon">→</span>
      Заказать
    </button>
  </div>
</template>

<script setup lang="ts">
import Flower from '~/assets/images/flower.png';
const emit = defineEmits(["open-modal"]);
const flowerImage = Flower;
</script>

<style scoped>
.hero-card {
  border-radius: 16px;
  padding: 2rem;
  box-sizing: border-box;
  flex: 1;
  position: relative;
  overflow: hidden;
  background: linear-gradient(135deg, #5c6cff 0%, #8d2bff 100%);
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.hero-card--right {
  position: relative;
  overflow: hidden;
  background-image: linear-gradient(rgba(8, 4, 161, 0.8), rgba(8, 4, 161, 0.8)), url('~/assets/images/flower.png');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  align-items: center;
  text-align: center;
  width: 950px;
  height: 600px;
  justify-content: space-between;
  border-radius: 16px 16px 16px 24px;
  padding: 70px;
  overflow: visible;
}
.hero-card--right::before {
  content: "Топ-10 самых креативных\Aразработчиков сайтов в России";
  white-space: pre-line;
  text-align: left;
  position: absolute;
  bottom: 0;
  left: 0;
  background: #F2F2F4;
  border-radius: 0 2rem 0 0;
  /* clip-path: inset(0 0 0 0 round 0 2rem 0 0); */
  padding: 0.5rem;
  font-size: 1rem;
  color: #000;
}

.hero-card--right > * {
  position: relative;
  z-index: 1;
}
.hero-support {
  position: absolute;
  top: 1rem;
  right: 1rem;
  color: #c5ff00;
  text-align: right;
  z-index: 2;
}
.hero-image {
  position: absolute;
  top: 0;
  right: -9rem;
  height: 100%;
  object-fit: cover;
  z-index: 1;
  max-height: none;
}
.hero-price-label {
  display: none;
}
.hero-price {
  position: absolute;
  bottom: 5rem;
  left: 4rem;
  font-size: 4rem;
  font-weight: 700;
  color: #fff;
  z-index: 2;
}
.hero-cta {
  position: absolute;
  bottom: 2rem;
  right: 2rem;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  background: #fff;
  color: #000;
  border-radius: 9999px;
  z-index: 2;
  cursor: pointer;
}
.hero-cta .arrow-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 24px;
  height: 24px;
  border-radius: 50%;
  background: #c5ff00;
  color: #000;
  font-size: 0.875rem;
}

/* @media (min-width: 900px) and (max-width: 1000px) {
  .hero-card--right {
    width: 900px;
  }
} */

@media (max-width: 1000px) {
  .hero-card{
    box-sizing:content-box
  }
  .hero-card--right {
    width: 320px;
    height: 250px;
    padding: 1.5rem;
  }
  .hero-support {
    display: none;
  }
  .hero-image {
    position: static;
    width: 100%;
    height: auto;
    object-fit: cover;
    margin-bottom: 1rem;
  }
  .hero-price-label {
    display: block;
    font-size: 0.875rem;
    opacity: 0.9;
    margin-bottom: 0.5rem;
  }
  .hero-price {
    position: static;
    font-size: 2.5rem;
    margin: 0.5rem 0;
  }
  .hero-cta {
    position: static;
    width: 262px;
    margin-top: 1rem;
  }
}
@media (max-width: 1000px) {
  .hero-card--right::before { display: none; }
}
</style>
