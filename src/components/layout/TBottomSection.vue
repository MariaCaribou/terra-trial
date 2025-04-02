<script setup>
import TCard from '../ui/TCard.vue';
import TTimeline from '../ui/TTimeline.vue';
</script>

<template>
  <section class="body-section">
    <TTimeline progress="33%" />
    <TCard
      title="This is a card lorem ispum dolor sit"
      text="Lorem ipsum dolor sit amet consectetur. Sed pulvinar odio velit fermentum etiam consectetur pretium fringilla metus."
      :image-urls="['https://www.w3schools.com/html/pic_trulli.jpg', 'https://www.w3schools.com/html/img_girl.jpg']"
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