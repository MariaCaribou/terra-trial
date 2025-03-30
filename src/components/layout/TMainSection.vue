<script setup>
import TCard from '../ui/TCard.vue';
</script>

<template>
  <section>
    <TCard
      title="This is a card lorem ispum dolor sit"
      text="Lorem ipsum dolor sit amet consectetur. Sed pulvinar odio velit fermentum etiam consectetur pretium fringilla metus."
      background-color="#fff"
      :image-urls="['https://www.w3schools.com/html/pic_trulli.jpg']"
    />

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
  padding: 6rem 0;
  gap: 4rem;
}
</style>