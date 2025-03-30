<script setup>
import THeader from './components/layout/THeader.vue';
import THeroSection from './components/layout/THeroSection.vue';
import TMainSection from './components/layout/TMainSection.vue';
</script>

<template>
  <THeader :menu-items="['Store', 'Our Story', 'Journal']" />

  <THeroSection 
    title="Lorem Ipsum"
    text="Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Vestibulum vehicula mauris, orci vel faucibus ac tincidunt."
    image-url=""
  />

  <TMainSection />
</template>

<style scoped>

</style>
