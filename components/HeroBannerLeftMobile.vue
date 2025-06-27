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
      <span class="arrow-icon">↗</span>
    </button>
  </div>
</template>

<script setup lang="ts">
import project1 from '~/assets/images/project1.jpg'
import project2 from '~/assets/images/project2.png'
import project3 from '~/assets/images/project3.jpg'
import project4 from '~/assets/images/project4.png'
import project5 from '~/assets/images/project5.jpg'

const thumbnails = [
  project1,
  project2,
  project3,
  project4,
  project5
]
</script>

<style scoped>
.hero-card {
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
  justify-content: space-between;
}

.hero-cta--projects {
  width: 87%;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  gap: 0.5rem;
  height: 44px;
  padding: 0 1rem;
  background: #fff;
  color: #5c6cff;
  border: none;
  border-radius: 9999px;
  font-size: 0.875rem;
  font-weight: 600;
  margin-top: -10px;
  cursor: pointer;
  position: relative;  /* add to anchor arrow positioning */
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
</style>
