<template>
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
</template>

<script setup lang="ts">
import arrow from '~/assets/images/arrow.png';
const emit = defineEmits(["open-modal"]);
</script>

<style scoped>
.hero-flowers {
  position: absolute;
  bottom: 0;
  right: 0;
  width: auto;
  height: 125%;
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-end;
  height: 100%;
  width: 100%;
}

.hero-price-block {
  margin-bottom: 0;
}

.hero-card {
  /* box-sizing: border-box; */
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

.hero-price-label {
  margin-bottom: 0;
  padding-bottom: 0;

  font-family: 'Golos Text', sans-serif;
  font-weight: 400;
  font-size: 18px;
  line-height: 1.2;
  opacity: 0.9;
}

.hero-price {
  margin-bottom: 0;
  padding-bottom: 0;

  font-size: 2.5rem;
  font-weight: 700;
  margin: 0.5rem 0;
}

.hero-support {
  color: #c5ff00;
  font-size: 1rem;
  line-height: 1.2;
  margin-top: auto; /* Pushes it down */
  padding-bottom: 1rem;
}

.hero-cta {
  

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

.hero-cta .arrow-icon {
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
.hero-cta .arrow-icon img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  transform: scale(0.5);
}
</style>
