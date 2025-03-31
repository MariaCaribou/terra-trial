<script setup>
defineProps({
  logoUrl: {
    type: String,
  },
  navLinks: {
    type: Array,
  },
})
</script>

<template>
  <header>
    <img :src="logoUrl" alt="terra logo">
    <nav>
      <a v-for="(navLink, index) in navLinks" :key="index" href="#!">{{ navLink }}</a>
    </nav>
  </header>
</template>

<style scoped>
header {
  display: flex;
  padding: 1.625rem 8.188rem 1.625rem 2.813rem;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  background-color: var(--background-color-light);
}

img {
  max-width: 17.4rem;
}

nav {
  display: flex;
  gap: 1.5rem;
}

nav a {
  font-size: var(--text-size-m);
  text-decoration: none;
  color: var(--text-color-dark);
}
</style>