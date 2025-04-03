<script setup>
import { onMounted, onUnmounted, ref, watch } from 'vue'

const props = defineProps({
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
    default: '0%',
  },
  transitionDuration: {
    type: Number,
    required: false,
    default: 1500
  },
})

const elementRef = ref(null)    // Element ref for checking visibility (timeline-wrapper div)
const alreadyVisible = ref(false)
const percentageRef = ref('0%')

watch(alreadyVisible, (newValue) => {
  // When the timeline is shown in the screen (will just happen once),
  // animate from 0 to props.percentage
  if (newValue) {
    animatePercentage(0, parseInt(props.percentage), props.transitionDuration)
  }
})

// Animate using requestAnimationFrame instead of setInterval
// for performance reasons
const animatePercentage = (start, end, duration) => {
  let startTime

  // From https://gist.github.com/gre/1650294
  const easeInOutCubic = (t) => t<.5 ? 4*t*t*t : (t-1)*(2*t-2)*(2*t-2)+1
  
  // Function called each frame
  const updatePercentage = (timestamp) => {
    // Store the start time the first time the frame function is executed
    if (!startTime) startTime = timestamp

    const elapsed = timestamp - startTime
    const progress = Math.min(elapsed / duration, 1) // Ensure that the progress is between [0, 1]
    const easedProgress = easeInOutCubic(progress)
    const newValue = Math.floor(easedProgress * (end - start) + start) // Convert from range [0, 1] to range [start, end]

    // Update just percentageRef, since it's the only value used by the UI
    percentageRef.value = newValue + '%'

    // Keep animating if haven't the end value
    if (newValue < end) requestAnimationFrame(updatePercentage)
  }
  
  requestAnimationFrame(updatePercentage)
}

// From https://www.javascripttutorial.net/dom/css/check-if-an-element-is-visible-in-the-viewport/
const isInViewport = (element) => {
    const rect = element.getBoundingClientRect()

    return (
        rect.top >= 0 &&
        rect.left >= 0 &&
        rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &&
        rect.right <= (window.innerWidth || document.documentElement.clientWidth)
    )
}

const checkVisibility = () => {
  // Check only if it is not already visible, since we only want this to occur just once
  if (elementRef.value && !alreadyVisible.value) {
    alreadyVisible.value = isInViewport(elementRef.value)
  }
}

onMounted(() => {
  window.addEventListener('scroll', checkVisibility)
  window.addEventListener('resize', checkVisibility)
})

onUnmounted(() => {
  window.removeEventListener('scroll', checkVisibility)
  window.removeEventListener('resize', checkVisibility)
})
</script>

<template>
  <div ref="elementRef" class="timeline-wrapper">
    <h2>{{ title }}</h2>

    <div class="timeline-content">
      <div class="timeline-text">
        <span>{{ initialItem?.label }}</span>
        <span>{{ finalItem?.label }}</span>
      </div>

      <div class="timeline-background">
        <span class="timeline-percentage">{{ percentageRef }}</span>
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
  left: v-bind(percentageRef);
  transform: translate(-50%, -50%);
  color: var(--color-primary);
  font-size: var(--text-size-xl);
  font-weight: 500;
}

.timeline-foreground {
  height: 100%;
  width: v-bind(percentageRef);
  border-radius: 56.25rem;
  background-color: var(--color-primary);
}

.timeline-marker {
  position: absolute;
  top: 50%;
  left: v-bind(percentageRef);
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