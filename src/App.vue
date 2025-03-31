<script setup>
import TNavbar from './components/layout/TNavbar.vue';
import THeroSection from './components/layout/THeroSection.vue';
import TMainSection from './components/layout/TMainSection.vue';
import TBottomSection from './components/layout/TBottomSection.vue';
</script>

<template>
  <TNavbar logo-url="https://tf-frontend.netlify.app/images/v1/logo.svg" :nav-links="['Store', 'Our Story', 'Journal']" />

  <THeroSection 
    title="Lorem Ipsum"
    text="Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Vestibulum vehicula mauris, orci vel faucibus ac tincidunt."
    image-url="https://tf-frontend.netlify.app/images/v1/bgimage.png"
  />

  <TMainSection />
  
  <TBottomSection />
</template>

<style scoped>

</style>
