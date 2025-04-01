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
    <img class="left-shape" src="https://tf-frontend.netlify.app/images/v1/shapes-left.png" alt="left shape">
    <img class="right-shape" src="https://tf-frontend.netlify.app/images/v1/shapes-right.png" alt="right shape">
  </section>
</template>

<style scoped>
section {
  display: flex;
  position: relative;
  justify-content: center;
  align-items: center;
  height: clamp(35rem, 44vw, 40rem);
  background-color: #444f3c;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
}

.hero-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2rem;
  max-width: 36.5rem;
  width: 80%;
  text-align: center;
}

h1 {
  font-size: var(--text-size-xxl);
  color: var(--text-color-light);
  font-weight: 700;
  letter-spacing: 1px;
}

p {
  font-size: var(--text-size-l);
  text-align: center;
  color: var(--text-color-light);
  letter-spacing: 0.2px;
}

.left-shape {
  position: absolute;
  bottom: 0;
  left: 0;
  width: clamp(20rem, 30vw, 27.6rem);
}

.right-shape {
  position: absolute;
  top: 0;
  right: 0;
  width: clamp(20rem, 30vw, 27.6rem);
}

@media only screen and (max-width: 600px) {
  section {
    padding-top: 2rem;
  }
}
</style>