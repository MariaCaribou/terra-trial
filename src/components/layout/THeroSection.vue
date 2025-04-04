<script setup>
import { ref, onMounted, inject } from 'vue'
import TButton from '../ui/TButton.vue'

// Reactive state to track if this is the first visit
const isFirstVisit = ref(true)

const heroData = inject('heroData')

const checkPreviousVisits = () => {
  const hasVisitedBefore = localStorage.getItem('hasVisitedBefore')
  
  if (hasVisitedBefore) {
    isFirstVisit.value = false
  } else {
    localStorage.setItem('hasVisitedBefore', 'true')
    isFirstVisit.value = true
  }
}

onMounted(() => {
  checkPreviousVisits()
})
</script>

<template>
  <section class="background-cover-center" :style="{ backgroundImage: 'url(' + heroData?.bg_image + ')' }">
    <div class="hero-content">
      <h1>{{ isFirstVisit ? heroData?.title?.first_time_accessing : heroData?.title?.second_time_accessing }}</h1>
      <p>{{ heroData?.subtitle }}</p>
      <TButton 
        :label="isFirstVisit ? heroData?.button_label?.first_time_accessing :
        heroData?.button_label?.second_time_accessing"
        :background-color="isFirstVisit ? '#189B5C' : '#0F0F0F'"
        :link="heroData?.button_link"
      />
    </div>
    <img class="left-shape" :src="heroData?.shapes?.shape_1" alt="left shape">
    <img class="right-shape" :src="heroData?.shapes?.shape_2" alt="right shape">
  </section>
</template>

<style scoped>
section {
  display: flex;
  position: relative;
  justify-content: center;
  align-items: center;
  height: clamp(35rem, 44vw, 40rem);
  background-color: #444f3c;
}

.hero-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
  max-width: 36.5rem;
  width: 80%;
  text-align: center;
}

h1 {
  font-size: var(--text-size-xxl);
  color: var(--text-color-light);
  font-weight: 700;
  letter-spacing: 1px;
}

p {
  text-align: center;
  color: var(--text-color-light);
  letter-spacing: 0.2px;
}

.left-shape {
  position: absolute;
  bottom: 0;
  left: 0;
  width: clamp(20rem, 30vw, 27.6rem);
}

.right-shape {
  position: absolute;
  top: 0;
  right: 0;
  width: clamp(20rem, 30vw, 27.6rem);
}

@media only screen and (max-width: 600px) {
  section {
    padding-top: 2rem;
  }
}
</style>