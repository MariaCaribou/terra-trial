<script setup>
import TPill from './TPill.vue';

defineProps({
  imageUrl: {
    type: String,
  }
})
</script>

<template>
  <div :style="{ backgroundImage: 'url(' + imageUrl + ')' }">
    <TPill position="top-right" />
  </div>
</template>

<style scoped>
div {
  display: block;
  width: 100%;
  height: 100%;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
}
</style>