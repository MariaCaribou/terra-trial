<script setup>
import TPill from './TPill.vue'

defineProps({
  date: {
    type: String,
  },
  type: {
    type: String,
    validator: (value) => {
      return ['Type A', 'Type B'].includes(value)
    }
  },
  title: {
    type: String,
  },
  imageUrl: {
    type: String,
  },
})
</script>

<template>
  <div class="post">
    <div class="image background-cover-center" :style="{ backgroundImage: 'url(' + imageUrl + ')' }">
      <TPill 
        text="Type Pill" 
        :background-color="type === 'Type B' ? '#F78BD8' : undefined"
      />
    </div>
    
    <span class="date">{{ date }}</span>

    <p>{{ title }}</p>
  </div>
</template>

<style scoped>
.post {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  height: 100%;
  width: 17.25rem;
  text-align: left;
}

.image {
  display: block;
  position: relative;
  height: 70%;
}

.date {
  font-size: var(--text-size-s);
  font-weight: 700;
}

p {
  line-height: 1.3;
}
</style>