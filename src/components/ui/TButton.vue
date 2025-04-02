<script setup>
defineProps({
  label: {
    type: String,
  },
  labelColor: {
    type: String,
    required: false,
    default: "#fff",
  },
  backgroundColor: {
    type: String,
    required: false,
    default: "#189B5C",
  },
  link: {
    type: String,
    required: false,
  }
})
</script>

<template>
  <a :href="link">{{label}}</a>
</template>

<style scoped>
a {
  position: relative;
  padding: 1rem 2.5rem;
  line-height: 1.75;
  font-size: var(--text-size-m);
  background-color: v-bind(backgroundColor);
  color: v-bind(labelColor);
  text-decoration: none;
  cursor: pointer;
  transition: background-color 0.25s ease-in-out;
  z-index: 5;
}

a:hover {
  background-color: var(--color-accent);
}
</style>