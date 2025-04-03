<script setup>
import TPill from './TPill.vue'

defineProps({
  imageUrl: {
    type: String,
  },
  pillLabel: {
    type: String,
  },
})
</script>

<template>
  <div class="background-cover-center" :style="{ backgroundImage: 'url(' + imageUrl + ')' }">
    <TPill :label="pillLabel" position="top-right" />
  </div>
</template>

<style scoped>
div {
  display: block;
  width: 100%;
  height: 100%;
}
</style>