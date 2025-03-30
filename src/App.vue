<script setup>
import TMenu from './components/TMenu.vue';
import THeroSection from './components/THeroSection.vue';
import TInfoSection from './components/TInfoSection.vue';
</script>

<template>
  <TMenu :menu-items="['Store', 'Our Story', 'Journal']" />

  <THeroSection 
    title="Lorem Ipsum"
    message="Lorem ipsum dolor sit amet, consectetur adipiscing elit.
    Vestibulum vehicula mauris, orci vel faucibus ac tincidunt."
    image=""
  />

  <TInfoSection/>
</template>

<style scoped>

</style>
