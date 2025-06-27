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
    <div class="hero-thumbnails">
      <img
        v-for="(thumb, idx) in thumbnails"
        :key="idx"
        :src="thumb"
        alt="project thumbnail"
        class="thumb"
      />
      <div class="hero-thumbnails__label">Наши<br/>Проекты</div>
    </div>
    <!-- Mobile-only CTA -->
    <button class="hero-cta hero-cta--projects">
      Наши проекты
      <span class="arrow-icon">↗</span>
    </button>
  </div>
</template>

<script setup lang="ts">
import project1 from '~/assets/images/project1.jpg';
import project2 from '~/assets/images/project2.png';
import project3 from '~/assets/images/project3.jpg';
import project4 from '~/assets/images/project4.png';
import project5 from '~/assets/images/project5.jpg';

const thumbnails = [
  project1,
  project2,
  project3,
  project4,
  project5
];
</script>

<style scoped>
.hero-card {
  width: 90%;
  aspect-ratio: 847 / 600;
  border-radius: 20px;
  padding: 60px;
  box-sizing: border-box;
  position: relative;
  overflow: hidden;
  background: linear-gradient(108.96deg, #0804A1 -2.15%, #9278FA 137.97%);
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.hero-badge {
  font-family: 'Golos Text', sans-serif;
  font-weight: 400;
  font-size: 18px;
  line-height: 120%;
  letter-spacing: 0%;
  opacity: 0.9;
  margin-bottom: 1rem;
  text-transform: none;
}
.hero-title {
  font-family: 'Golos Text', sans-serif;
  font-weight: 500;
  font-size: 28px;
  line-height: 120%;
  letter-spacing: 0%;
  text-transform: uppercase;
  margin: 0 0 1.5rem 0;
}
.hero-thumbnails {
  display: flex;
  gap: 0.5rem;
  flex-wrap: nowrap;
  align-items: flex-end;
  position: relative;
  padding: 1rem;
  border-radius: 8px;
  /* width:  728px; */
  height: clamp(100px, 12vw, 134px);
  margin-top: auto;
}

/* Background layer with cutout */
.hero-thumbnails::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: #fff;
  border-radius: 8px;
  mask: radial-gradient(circle at top right, transparent 35px, #fff 35px);
  -webkit-mask: radial-gradient(circle at top right, transparent 35px, #fff 35px);
  z-index: 1;
}

/* Ensure content is above background */
.hero-thumbnails > * {
  position: relative;
  z-index: 2;
}

.thumb {
  width: clamp(80px, 10vw, 114px);
  height: clamp(80px, 10vw, 112px);
  border-radius: 4px;
  object-fit: cover;
}
.hero-thumbnails__label { 
  margin-left: 0.5rem;
  height: clamp(100px, 12vw, 134px);
  display: flex;
  align-items: flex-end;
  

  font-family: 'Golos Text', sans-serif;
  font-weight: 500;
  font-size: 16px;
  line-height: 120%;
  letter-spacing: 0%;

  color: #000;
  
}
.hero-thumbnails::after {
  content: '↗';
  position: absolute;
  top: -8px;
  right: -8px;
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  color: #000;
  background: #c5ff00;
  border-radius: 50%;
}
.hero-cta {
  padding: 0.75rem 1.5rem;
  border: none;
  border-radius: 24px;
  font-size: 1rem;
  background: #fff;
  color: #5c6cff;
  cursor: pointer;
  transition: background 0.2s ease;
}
.hero-cta:hover {
  background: #e6e6e6;
}
@media (max-width: 900px) {
  .hero-card {
    padding: 1.5rem;
    width: 90%;
    height: auto;
  }
  .hero-thumbnails {
    display: none;
  }
  .hero-cta--projects {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.75rem 1rem;
    background: #fff;
    color: #5c6cff;
    border: none;
    border-radius: 9999px;
    font-size: 0.875rem;
    font-weight: 600;
    width: 80%;
    height: 45px;
    margin: 1rem auto 0;
    cursor: pointer;
  }
  .arrow-icon {
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
  .hero-cta--projects {
    position: relative;
    overflow: visible;
  }
  .hero-cta--projects .arrow-icon {
    position: absolute;
    right: -0.75rem;
    top: 50%;
    transform: translateY(-50%);
  }
}
@media (min-width: 900px) {
  .hero-cta--projects {
    display: none;
  }
  .hero-card--left {
    flex: 2;
    padding: 3rem;
    background: linear-gradient(135deg, #1500FF 0%, #6C5AE0 100%);
  }
  .hero-card--left .hero-badge {
    text-transform: none;
    margin-bottom: 1rem;

    font-family: 'Golos Text', sans-serif;
    font-weight: 400;
    font-size: 20px;
    line-height: 100%;
    letter-spacing: 0%;
  }
  .hero-card--left .hero-title {
    font-size: 3.5rem;
    line-height: 1.2;
    margin-bottom: 2rem;
  }
}
@media (min-width: 900px) and (max-width: 1000px) {
  .hero-card--left {
    width: 900px;
    height: 450px;
  }
}
@media (max-width: 1000px) {
  .hero-card--left {
    width: 100%;
    height: 450px;
    padding: 1.5rem;
  }
}
</style>
