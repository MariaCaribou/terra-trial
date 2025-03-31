<script setup>
import TPill from './TPill.vue';

defineProps({
  imageUrls: {
    type: Array,
  }
})
</script>

<template>
  <div class="images-wrapper">
    <div></div>
    <div :style="{ backgroundImage: 'url(' + imageUrls[0] + ')' }"></div>
    <div :style="{ backgroundImage: 'url(' + imageUrls[1] + ')' }"></div>
    <div></div>

    <TPill position="bottom-right" />
  </div>
</template>

<style scoped>
.images-wrapper {
  display: flex;
  flex-wrap: wrap;
  height: 100%;
  width: 100%;
}

.images-wrapper div {
  width: 50%;
  height: 50%;
  background-color: var(--background-color-dark);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
}
</style>