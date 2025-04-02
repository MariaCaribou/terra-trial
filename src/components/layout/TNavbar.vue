<script setup>
import { onMounted, onUnmounted, ref } from 'vue';
import THamburgerButton from '../ui/THamburgerButton.vue';

defineProps({
  logoUrl: {
    type: String,
  },
  navLinks: {
    type: Array,
  },
})

const isMobileMenuOpen = ref(false)

function toggleMobileMenu() {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

function closeMobileMenu() {
  isMobileMenuOpen.value = false
}

onMounted(() => {
  window.addEventListener('resize', closeMobileMenu)
  window.addEventListener('scroll', closeMobileMenu)
})

onUnmounted(() => {
  window.removeEventListener('resize', closeMobileMenu)
  window.removeEventListener('scroll', closeMobileMenu)
})
</script>

<template>
  <header>
    <img :src="logoUrl" alt="terra logo">

    <THamburgerButton @click="toggleMobileMenu" :is-open="isMobileMenuOpen" />

    <nav :class="{ 'open': isMobileMenuOpen }">
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

@media only screen and (max-width: 992px) {
  header {
    padding-right: 2.813rem;
  }
}

@media only screen and (max-width: 600px) {
  header {
    position: fixed;
    top: 0;
    padding: 1rem;
    z-index: 10;
  }

  header::after {
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    left: 0;
    bottom: 0;
    background-color: var(--background-color-light);
    z-index: 9;
  }

  img {
    z-index: inherit;
  }

  nav {
    position: absolute;
    flex-direction: column;
    align-items: flex-end;
    gap: 1rem;
    top: 0;
    left: 0;
    right: 0;
    background-color: var(--background-color-light);
    padding: 1rem 2rem;
    transform: translateY(-100%);
    transition: all 0.33s ease-in-out;
    z-index: 8;
  }

  nav.open {
    transform: translateY(0%);
    top: 5rem; /* This is the fixed height of the header. Could be a dynamic value, but I'm keeping it simple. */
  }
}
</style>