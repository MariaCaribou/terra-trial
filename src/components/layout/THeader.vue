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
        <a href="#!">{{ menuItem }}</a>
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
  padding-right: 5rem;
  background-color: var(--background-color-light);
}

.menu-icons {
  display: flex;
  justify-content: space-between;
  max-width: 33%;
}

ul {
  display: flex;
  list-style: none;
  gap: 1.5rem;
}

li a {
  font-size: var(--text-size-m);
  text-decoration: none;
  color: var(--text-color-dark);
}
</style>