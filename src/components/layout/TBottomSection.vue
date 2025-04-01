<script setup>
import TCard from '../ui/TCard.vue';
import TTimeline from '../ui/TTimeline.vue';
</script>

<template>
  <section>
    <TTimeline progress="33" />
    <TCard
      title="This is a card lorem ispum dolor sit"
      text="Lorem ipsum dolor sit amet consectetur. Sed pulvinar odio velit fermentum etiam consectetur pretium fringilla metus."
      :image-urls="['https://www.w3schools.com/html/pic_trulli.jpg', 'https://www.w3schools.com/html/img_girl.jpg']"
    />
  </section>
</template>

<style scoped>
section {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 7.5rem;
  gap: 7rem;
  text-align: center;
}

@media only screen and (max-width: 768px) {
  section {
    padding: 4rem 2rem;
  }
}
</style>