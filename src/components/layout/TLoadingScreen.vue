<script setup>
import { defineProps, ref, watch } from 'vue'

// Store props in a variable for being able to watch it
const props = defineProps({
  isLoading: {
    type: Boolean,
    default: false,
  },
  delay: {
    type: Number,
    required: false,
    default: 600,
  },
  transitionDuration: {
    type: Number,
    required: false,
    default: 300
  },
})

const opacity = ref(1)
const height = ref('100%')

watch(() => props.isLoading, (newValue) => {
  // If isLoading is now false, do a chain of delays
  if (!newValue) {
    // 1. Set GIF opacity to 0
    setTimeout(() => {
      opacity.value = 0

      // 2. Set loading screen height to 0
      setTimeout(() => {
        height.value = '0'
      }, props.transitionDuration)
    }, props.delay)
  }
})
</script>

<template>
  <div class="loading-screen" :style="{ transitionDuration: props.transitionDuration + 'ms' }">
    <img
      :style="{ transitionDuration: props.transitionDuration + 'ms' }"
      src="https://terrahq.com/preloader/preloader.gif"
      alt="preloader media"
    >
  </div>
</template>

<style scoped>
.loading-screen {
  display: flex;
  position: fixed;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: var(--background-color-dark);
  top: 0;
  left: 0;
  height: v-bind(height);
  width: 100%;
  z-index: 100;
  transition: height ease-in-out;
}

img {
  opacity: v-bind(opacity);
  transition: opacity ease-in-out;
  width: 85%;
  max-width: 18.75rem;
}
</style>