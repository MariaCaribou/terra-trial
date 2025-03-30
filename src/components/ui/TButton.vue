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
})
</script>

<template>
  <span>{{label}}</span>
</template>

<style scoped>
span {
  padding: 1rem 2.5rem;
  line-height: 1.75;
  font-size: var(--text-size-m);
  background-color: v-bind(backgroundColor);
  color: v-bind(labelColor);
  cursor: pointer;
}
</style>