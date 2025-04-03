<script setup>
import { ref, onMounted, provide, computed, readonly } from 'vue'
import TNavbar from './components/layout/TNavbar.vue';
import THeroSection from './components/layout/THeroSection.vue';
import TMainSection from './components/layout/TMainSection.vue';
import TBottomSection from './components/layout/TBottomSection.vue';
import TLoadingScreen from './components/layout/TLoadingScreen.vue';

// Fetch states
const data = ref(null)
const loading = ref(false)
const error = ref(null)

// Provide/inject pattern to avoid prop drilling.
provide('navbarData', readonly(computed(() => data?.value?.navbar)))
provide('heroData', readonly(computed(() => data?.value?.hero)))
provide('introCardData', readonly(computed(() => data?.value?.intro_card)))
provide('blogData', readonly(computed(() => data?.value?.blog)))
provide('timelineData', readonly(computed(() => data?.value?.timeline)))
provide('ctaData', readonly(computed(() => data?.value?.cta)))

const fetchData = async () => {
  loading.value = true
  error.value = null
  
  try {
    const response = await fetch('https://tf-frontend.netlify.app/trial')
    
    if (!response.ok) {
      throw new Error(`Error HTTP: ${response.status}`)
    }

    data.value = await response.json()
  } catch (err) {
    error.value = err.message || 'Error loading data'
    console.error(err)
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  fetchData()
})
</script>

<template>
  <TLoadingScreen :is-loading="loading" />
  <TNavbar />
  <THeroSection />
  <TMainSection /> 
  <TBottomSection />
</template>

<style scoped>

</style>
