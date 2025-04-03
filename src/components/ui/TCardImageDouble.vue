<script setup>
import TPill from './TPill.vue'

defineProps({
  imageUrls: {
    type: Array,
  },
  pillLabel: {
    type: String,
  },
})
</script>

<template>
  <div class="images-wrapper">
    <div></div>
    <div class="background-cover-center" :style="{ backgroundImage: 'url(' + imageUrls[0] + ')' }"></div>
    <div class="background-cover-center" :style="{ backgroundImage: 'url(' + imageUrls[1] + ')' }"></div>
    <div></div>

    <TPill :label="pillLabel" position="bottom-right" />
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
}
</style>