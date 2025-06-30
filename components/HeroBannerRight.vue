<template>
  <div class="hero-card hero-card--right">
    <p class="hero-support">техподдержка сайта<br />на 30 дней — в подарок</p>
    <img :src="flowerImage" alt="flower" class="hero-image" />
    <p class="hero-price-label">ваша цена</p>
    <div class="hero-price">320 000 ₽</div>
    <button class="hero-cta" @click="emit('open-modal')">
      <span class="arrow-icon"><img :src="arrow" alt="arrow" /></span>
      Заказать
    </button>
  </div>
</template>

<script setup lang="ts">
import Flower from '~/assets/images/flower.png';
import arrow from '~/assets/images/arrow.png';
const emit = defineEmits(["open-modal"]);
const flowerImage = Flower;
</script>

<style scoped>
.hero-card {
  /* border-radius: 16px; */
  padding: 2rem;
  box-sizing: border-box;
  flex: 1;
  position: relative;
  /* overflow: hidden; */
  background: linear-gradient(135deg, #5c6cff 0%, #8d2bff 100%);
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.hero-card--right {
  flex: 1;
  /* Responsive flex layout */
  background: url('../assets/images/RightBanner.svg') center/cover no-repeat;
  border-radius: 16px 16px 16px 0px;
  padding: 2rem;
  align-items: center;
  text-align: center;
}








.hero-card--right::before {
  content: "Топ-10 самых креативных\Aразработчиков сайтов в России";
  white-space: pre-line;
  text-align: left;
  position: absolute;
  bottom: 0;
  left: 1rem;
  background: #F2F2F4;
  z-index: 1000;
  font-size: 1rem;
  color: #000;

  /* clip-path: polygon(0% 1%, 14% 17%, 91% 18%, 100% 100%, 0% 99%); */
  /* clip-path: ellipse(25% 27% at 50% 50%); */
  /* clip-path: ellipse(25% 27% at 50% 50%); */
}













.hero-card--right > * {
  position: relative;
  z-index: 1;
}
.hero-support {
  position: absolute;
  top: 3rem;
  right: 2rem;
  color: #c5ff00;
  text-align: right;
  z-index: 2;
}
.hero-image {
  position: absolute;
  top: 0;
  right: -8rem;
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
  bottom: 0;
  right: 0;
  margin: 1rem;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  background: #fff;
  color: #000;
  border-radius: 9999px;
  border: none;
  outline: none;
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
    position: absolute;
    top: 0;
    right: 0;
    height: 100%;
    width: auto;
    object-fit: cover;
    margin-bottom: 0;
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
.hero-cta .arrow-icon img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  transform: scale(0.5);
}
</style>
