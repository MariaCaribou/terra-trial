<script setup>
defineProps({
  menuItems: {
    type: Array,
  }
})
</script>

<template>
  <header>
    <div class="menu-icons"></div>
    <ul>
      <li v-for="(menuItem, index) in menuItems" :key="index">
        {{ menuItem }}
      </li>
    </ul>
  </header>
</template>

<style scoped>
  header {
    display: flex;
    padding: 1rem;
    justify-content: space-between;
    width: 100%;
  }

  .menu-icons {
    display: flex;
    justify-content: space-between;
    max-width: 33%;
  }

  ul {
    display: flex;
    list-style: none;
    gap: 0.5rem;
  }

  li {
    font-size: var(--text-size-m);
    font-family: "Manrope", sans-serif;
  }
</style>