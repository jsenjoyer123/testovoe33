<template>
  <nav class="menu">
    <div class="menu__inner">
      <button v-if="!isModalOpen" class="menu__burger" @click="toggleMenu">
        <span>&#9776;</span>
      </button>
    <div class="menu__group menu__group--left">
      <button class="menu__item menu__item--with-badge">
        Проекты
        <span class="menu__badge">18</span>
      </button>
      <button class="menu__item menu__item--with-badge menu__item--dropdown">
        Услуги
        <span class="menu__badge">36</span>
      </button>
      <button class="menu__item menu__item--dropdown">Мы</button>
    </div>
    <div class="menu__logo">
      <picture>
        <source :srcset="mobileLogo" media="(max-width: 1000px)" />
        <img :src="logo" alt="ACOOLA TEAM Logo" class="menu__logo-img" />
      </picture>
    </div>
    <div class="menu__group menu__group--right">
      <button class="menu__item menu__item--with-badge">
        Блог
        <span class="menu__badge">31</span>
      </button>
      <button class="menu__item">Контакты</button>
      <button class="menu__item menu__item--cta" @click="emit('open-modal')">
  <span class="menu__item--cta-text">
    <span class="cta-desktop">Связаться с нами</span>
    <span class="cta-mobile">Напишите нам</span>
  </span>
</button>
    </div>
      </div>
    <div v-if="isOpen" class="menu__mobile-dropdown">
      <div class="menu__group menu__group--mobile">
        <button class="menu__item menu__item--with-badge">Проекты<span class="menu__badge">18</span></button>
        <button class="menu__item menu__item--with-badge menu__item--dropdown">Услуги<span class="menu__badge">36</span></button>
        <button class="menu__item menu__item--dropdown">Мы</button>
        <button class="menu__item menu__item--with-badge">Блог<span class="menu__badge">31</span></button>
        <button class="menu__item">Контакты</button>
      </div>
    </div>
  </nav>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import logo from '~/assets/images/logo.png';
import mobileLogo from '~/assets/images/mobilelogo.png';
const { isModalOpen } = defineProps<{ isModalOpen: boolean }>();
const emit = defineEmits(['open-modal']);
const isOpen = ref(false);
const toggleMenu = () => {
  isOpen.value = !isOpen.value;
};
</script>

<style scoped>
.cta-mobile { display: none; }
.cta-desktop { display: inline; }
/* Import Inter font if not globally available */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700&display=swap');

.menu {
  position: relative;
  
  /* padding: 16px 40px; */
  background-color: #FFFFFF;
  font-family: 'Inter', sans-serif;
  /* full-width menu */
    width: 100%;
  margin: 0;
  height: 67px; /* Set height to 67px for desktop */
}

.menu__inner {
  display: flex;
  justify-content: space-between; /* Distribute space between groups */
  align-items: center;
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 40px;
  height: 100%;
}

.menu__group {
  display: flex;
  align-items: center;
}

.menu__group--left {
  display: flex;
  gap: 24px;
  flex: 1; /* Allow to grow */
  justify-content: flex-start; /* Align to left */
}

.menu__logo {
  display: flex;
  justify-content: center; /* Center logo */
  flex: 0 1 auto; /* Don't grow or shrink */
}

.menu__group--right {
  display: flex;
  gap: 24px;
  flex: 1; /* Allow to grow */
  justify-content: flex-end; /* Align to right */
}

.menu__logo-main {
  font-size: 32px;
  font-weight: 700;
  color: #111827;
  letter-spacing: 0.1em;
  line-height: 1;
}

.menu__logo-sub {
  font-size: 14px;
  color: #6B7280;
  letter-spacing: 0.2em;
}

.menu__item {
  position: relative;
  background: none;
  border: 1px solid #e5e7eb; /* Add border to buttons */
  max-width: 1280px; /* Set max-width as requested */
  box-sizing: border-box; /* Include border in element dimensions */
  font-size: 14px;
  font-weight: 500;
  color: #4B5563;
  cursor: pointer;
  padding: 8px 16px;
  border-radius: 9999px;
  transition: background-color 0.2s ease-in-out, color 0.2s ease-in-out;
  display: flex;
  align-items: center;
  gap: 6px;
}

.menu__item:hover {
  border-color: #d1d5db; /* Change border color on hover */
  background-color: #F3F4F6;
  color: #111827;
}

.menu__item--with-badge {
  /* reset vertical offset */
  margin-top: 0;
}

.menu__badge {
  position: absolute;
  top: 0;
  right: 0;
  transform: none;
  background-color: #F3F4F6;
  color: #8B5CF6;
  font-size: 10px;
  font-weight: 500;
  padding: 1px 5px;
  border-radius: 6px;
}

.menu__item--dropdown::after {
  content: '';
  display: inline-block;
  width: 7px;
  height: 7px;
  border-left: 1.5px solid #9CA3AF;
  border-bottom: 1.5px solid #9CA3AF;
  transform: rotate(-45deg);
  margin-left: 4px;
  margin-bottom: 2px;
}

.menu__item--cta {
  background-color: #252525;
  color: #FFFFFF;
  border-radius: 9999px;
  padding: 12px 24px;
  margin-top: 0; /* Reset margin for cta button */
}

.menu__item--cta:hover {
  background-color: #404040;
  color: #FFFFFF;
}

.menu__item--cta:active {
  background-color: #FDE047;
  color: #111827;
}
.menu__burger {
  display: none;
}

@media (max-width: 1000px) {
  .menu__inner { justify-content: space-between; }
  .menu__group--right, .menu__logo, .menu__burger { flex: 0; }
  .menu {
    height: auto; /* Reset height for mobile */
  }
  .menu__burger {
    display: inline-flex;
    background: none;
    border: none;
    font-size: 24px;
    cursor: pointer;
    margin-right: 16px;
    z-index: 1;
  }
  .menu__group.menu__group--left,
  .menu__group.menu__group--right button:not(.menu__item--cta) {
    display: none;
  }
  .menu__mobile-dropdown {
    display: flex;
    flex-direction: column;
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    background-color: #FFFFFF;
    padding: 16px;
    gap: 8px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    z-index: 10000;
  }
  .menu__mobile-dropdown .menu__item {
    font-size: 12px;
    padding: 6px 12px;
  }
}
.menu__logo-img {
  width: 140px;
  height: auto;
}

@media (max-width: 1000px) {
  .cta-desktop { display: none; }
  .cta-mobile { display: inline; }

  .menu__logo-img {
    width: 78px;
    height: auto;
  }

  .menu__item--cta {
    width: 150px;
    height: 45px;
    gap: 10px;
    border-radius: 30px;
    padding-top: 13px;
    padding-right: 26px;
    padding-bottom: 12px;
    padding-left: 26px;
    justify-content: center;
  }
  .menu__item--cta-text {
    font-family: 'Gilroy', sans-serif;
    font-weight: 600;
    font-size: 16px;
    line-height: 100%;
    letter-spacing: 0%;
    white-space: nowrap;
  }

}
</style>
