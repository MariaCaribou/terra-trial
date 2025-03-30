<script setup>
import TButton from '../ui/TButton.vue';

defineProps({
  title: {
    type: String,
  },
  text: {
    type: String,
  },
  imageUrl: {
    type: String,
  }
})
</script>

<template>
  <section :style="{ backgroundImage: 'url(' + imageUrl + ')' }">
    <div class="hero-content">
      <h1>{{title}}</h1>
      <p>{{text}}</p>
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
  color: var(--text-color-light);
  font-weight: bold;
  letter-spacing: 1px;
}

p {
  font-size: var(--text-size-l);
  text-align: center;
  color: var(--text-color-light);
  letter-spacing: 0.2px;
}
</style>