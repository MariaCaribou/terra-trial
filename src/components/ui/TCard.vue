<script setup>
import TCardImageDouble from './TCardImageDouble.vue';
import TCardImageSingle from './TCardImageSingle.vue';

defineProps({
  title: {
    type: String,
  },
  text: {
    type: String,
  },
  backgroundColor: {
    type: String,
    required: false,
    default: 'transparent',
  },
  imageUrls: {
    type: Array,
    default: []
  }
})
</script>

<template>
  <div class="card">
    <div class="left-side">
      <div class="left-side-content">
        <h2>{{title}}</h2>
        <p>{{text}}</p>
      </div>
    </div>
    
    <div class="right-side">
      <TCardImageSingle
        v-if="imageUrls && imageUrls.length === 1"
        :image-url="imageUrls[0]"
      />

      <TCardImageDouble
        v-if="imageUrls && imageUrls.length > 1"
        :image-urls="imageUrls"
      />
    </div>
  </div>
</template>

<style scoped>
.card {
  display: flex;
  max-width: 75.5rem;
  width: 100%;
  height: 27.313rem;
}

.left-side,
.right-side {
  width: 50%;
}

.left-side {
  background-color: var(--background-color-dark);
}

.left-side-content {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  background-color: v-bind(backgroundColor);
  height: 85%;
  padding: 4rem;
}

h2 {
  font-size: var(--text-size-xl);
  font-weight: 700;
  line-height: 1.3;
}

p {
  font-size: var(--text-size-l);
  line-height: 1.4;
}

.right-side {
  position: relative;
}
</style>