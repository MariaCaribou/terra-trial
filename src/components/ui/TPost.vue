<script setup>
import TPill from './TPill.vue';

defineProps({
  date: {
    type: Date,
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
    <div class="image" :style="{ backgroundImage: 'url(' + imageUrl + ')' }">
      <TPill 
        text="Type Pill" 
        :background-color="type === 'Type B' ? '#F78BD8' : undefined"
      />
    </div>
    
    <span class="date">{{date}}</span>

    <p>{{title}}</p>
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
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
}

.date {
  font-size: var(--text-size-s);
  font-weight: 700;
}

p {
  font-size: var(--text-size-l);
  line-height: 1.3;
}
</style>