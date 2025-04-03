<script setup>
import { inject } from 'vue'
import TCard from '../ui/TCard.vue'
import TTimeline from '../ui/TTimeline.vue'

const timelineData = inject('timelineData')
const ctaData = inject('ctaData')
</script>

<template>
  <section class="body-section">
    <TTimeline 
      :title="timelineData?.title" 
      :initial-item="timelineData?.initial_item"
      :final-item="timelineData?.final_item"
      :percentage="timelineData?.percentage"
    />
    <TCard
      :title="ctaData?.title"
      :text="ctaData?.subtitle"
      :image-urls="[ctaData?.image_1, ctaData?.image_2]"
      :pill-label="ctaData?.pill"
    />
  </section>
</template>

<style scoped>
section {
  padding: 7.5rem;
  gap: 7rem;
  text-align: center;
}
</style>