<script setup>
import { ref, onMounted, provide, watchEffect } from 'vue'
import TNavbar from './components/layout/TNavbar.vue';
import THeroSection from './components/layout/THeroSection.vue';
import TMainSection from './components/layout/TMainSection.vue';
import TBottomSection from './components/layout/TBottomSection.vue';

// Fetch states
const navbarData = ref(null)
const heroData = ref(null)
const introCardData = ref(null)
const blogData = ref(null)
const timelineData = ref(null)
const ctaData = ref(null)

const loading = ref(false)
const error = ref(null)

// Provide/inject pattern to avoid prop drilling.
provide('navbarData', navbarData)
provide('heroData', heroData)
provide('introCardData', introCardData)
provide('blogData', blogData)
provide('timelineData', timelineData)
provide('ctaData', ctaData)

const fetchData = async () => {
  loading.value = true
  error.value = null
  
  try {
    const response = await fetch('https://tf-frontend.netlify.app/trial')
    
    if (!response.ok) {
      throw new Error(`Error HTTP: ${response.status}`)
    }

    const parsedData = await response.json()

    navbarData.value = parsedData.navbar
    heroData.value = parsedData.hero
    introCardData.value = parsedData.intro_card
    blogData.value = parsedData.blog
    timelineData.value = parsedData.timeline
    ctaData.value = parsedData.cta
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
  <TNavbar />
  <THeroSection />
  <TMainSection /> 
  <TBottomSection />
</template>

<style scoped>

</style>
