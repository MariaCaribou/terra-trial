<script setup>
defineProps({
  title: {
    type: String,
  },
  initialItem: {
    type: Object,
  },
  finalItem: {
    type: Object,
  },
  percentage: {
    type: String,
  },
})
</script>

<template>
  <div class="timeline-wrapper">
    <h2>{{ title }}</h2>
    <div class="timeline-content">
      <div class="timeline-text">
        <span>{{ initialItem?.label }}</span>
        <span>{{ finalItem?.label }}</span>
      </div>

      <div class="timeline-background">
        <span class="timeline-percentage">{{ percentage }}</span>
        <div class="timeline-foreground"></div>
        <div class="timeline-marker"></div>
      </div>

      <div class="timeline-numbers">
        <span>{{ initialItem?.data }}</span>
        <span>{{ initialItem?.data }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.timeline-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 9rem;
  width: 100%;
  max-width: 62.6rem;
}

.timeline-content {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  width: 100%;
}

.timeline-text,
.timeline-numbers {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.timeline-text {
  font-size: var(--text-size-l);
  font-weight: 500;
  line-height: 1.4;
}

.timeline-background {
  position: relative;
  width: 100%;
  height: 1rem;
  border-radius: 56.25rem;
  background-color: var(--color-secondary);
}

.timeline-percentage {
  position: absolute;
  top: calc(50% - 3.5rem);
  left: v-bind(percentage);
  transform: translate(-50%, -50%);
  color: var(--color-primary);
  font-size: var(--text-size-xl);
  font-weight: 500;
}

.timeline-foreground {
  height: 100%;
  width: v-bind(percentage);
  border-radius: 56.25rem;
  background-color: var(--color-primary);
}

.timeline-marker {
  position: absolute;
  top: 50%;
  left: v-bind(percentage);
  transform: translate(-50%, -50%);
  width: 2.5rem;
  height: 2.5rem;
  border-radius: 50%;
  background-color: var(--color-primary);
}

.timeline-numbers span:first-child {
  font-size: var(--text-size-xl);
  color: var(--color-primary);
  font-weight: 500;
}

.timeline-numbers span:last-child {
  font-size: var(--text-size-xxl);
  font-weight: 700;
}
</style>