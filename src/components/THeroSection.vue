<script setup>
import TButton from './TButton.vue';

defineProps({
  title: {
    type: String,
  },
  message: {
    type: String,
  },
  imageURL: {
    type: String,
  }
})
</script>

<template>
  <section>
    <div class="hero-content">
      <h1>{{title}}</h1>
      <span>{{message}}</span>
      <TButton 
        label="Button Label"
      />
    </div>
  </section>
</template>

<style scoped>
  section {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 40rem;
    background-color: #444f3c;
    background-image: v-bind(imageURL);
  }

  .hero-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
    max-width: 40%;
  }

  h1 {
    font-size: var(--text-size-xxl);
    color: white;
    font-weight: bold;
    letter-spacing: 1px;
  }

  span {
    font-size: var(--text-size-l);
    text-align: center;
    color: white;
    letter-spacing: 0.2px;
  }
</style>