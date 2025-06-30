<template>
  <section class="hero-banner">
    <div class="hero-banner__content">
      <template v-if="!isMobile">
        <HeroBannerLeft />
        <HeroBannerRight @open-modal="emit('open-modal')" />
      </template>
      <template v-else>
        <HeroBannerMobile @open-modal="emit('open-modal')" />
      </template>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue';
import HeroBannerLeft from '~/components/HeroBannerLeft.vue';
import HeroBannerRight from '~/components/HeroBannerRight.vue';
import HeroBannerMobile from '~/components/HeroBannerMobile.vue';
const emit = defineEmits(["open-modal"]);

const isMobile = ref(false);
const checkMobile = () => { isMobile.value = window.innerWidth < 900; };
onMounted(() => { checkMobile(); window.addEventListener('resize', checkMobile); });
onBeforeUnmount(() => { window.removeEventListener('resize', checkMobile); });
</script>

<style scoped>
.hero-banner {
  padding: 2rem 0;
}
.hero-banner__content {
  max-width: 1280px;
  margin: 0 auto;
  display: flex;
  gap: 1rem;
  overflow: hidden;
}


@media (max-width: 900px) {
  .hero-banner__content {
    flex-direction: column;
  }
}
@media (min-width: 900px) and (max-width: 1000px) {
  .hero-banner__content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;
    width: 900px;
    margin: 0 auto;
  }
}
</style>
