<script setup>
defineProps({
  isOpen: {
    type: Boolean,
    default: false
  },
})
</script>``

<template>
  <div class="hamburger" :class="{ 'open': isOpen }">
    <span class="hamburger-top-bun"></span>
    <span class="hamburger-bottom-bun"></span>
  </div>
</template>

<style scoped>
.hamburger {
  display: none;
  cursor: pointer;
}

@media only screen and (max-width: 600px) {
  .hamburger {
    position: relative;
    display: block;
    width: 3rem;
    height: 3rem;
    transition: all 0.25s;
    z-index: inherit;
  }

  .hamburger-top-bun,
  .hamburger-bottom-bun {
    content: '';
    display: block;
    position: absolute;
    left: 1rem;
    width: 1.125rem;
    height: 1px;
    background: var(--text-color-dark);
    transform: rotate(0);
    transition: all 0.25s;
  }

  .hamburger-top-bun {
    top: 1.4rem;
    transform: translateY(-0.2rem);
  }

  .hamburger-bottom-bun {
    bottom: 1.4rem;
    transform: translateY(0.2rem);
  }

  .hamburger.open {
    transform: rotate(90deg);
  }

  .hamburger.open .hamburger-top-bun {
    transform: rotate(45deg) translateY(0.1rem);
  }

  .hamburger.open .hamburger-bottom-bun {
    transform: rotate(-45deg) translateY(-0.1rem);
  }
}
</style>