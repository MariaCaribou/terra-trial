<script setup>
defineProps({
  text: {
    type: String,
    required: false,
    default: 'Pill Label',
  },
  textColor: {
    type: String,
    required: false,
    default: '#fff',
  },
  backgroundColor: {
    type: String,
    required: false,
    default: '#189B5C',
  },
  position: {
    type: String,
    required: false,
    default: 'top-left',
    validator: (value) => {
      return ['top-left', 'top-right', 'bottom-left', 'bottom-right'].includes(value)
    }
  }
})
</script>

<template>
  <span :class="position">{{ text }}</span>
</template>

<style scoped>
span {
  display: block;
  position: absolute;
  padding: 0.5rem 0.75rem;
  background-color: v-bind(backgroundColor);
  color: v-bind(textColor);
  border-radius: 1.188rem;
  font-size: var(--text-size-s);
}

.top-left {
  top: 1.5rem;
  left: 1.5rem;
}

.top-right {
  top: 1.5rem;
  right: 1.5rem;
}

.bottom-left {
  bottom: 1.5rem;
  left: 1.5rem;
}

.bottom-right {
  bottom: 1.5rem;
  right: 1.5rem;
}
</style>