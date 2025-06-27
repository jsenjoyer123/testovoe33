<template>
  <section class="hero-mobile">
    <HeroBannerLeftMobile />
    <HeroBannerRightMobile @open-modal="emit('open-modal')" />
  </section>
</template>

<script setup lang="ts">
import HeroBannerLeftMobile from '~/components/HeroBannerLeftMobile.vue';
import HeroBannerRightMobile from '~/components/HeroBannerRightMobile.vue';
const emit = defineEmits(['open-modal']);
</script>

<style scoped>
.hero-mobile {
  display: flex;
  flex-direction: column;
  align-items: center; /* Center the cards */
  gap: 1rem;
  padding: 1rem;
}
</style>
