<script setup>
import TCardImageDouble from './TCardImageDouble.vue'
import TCardImageSingle from './TCardImageSingle.vue'

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
    default: [],
  },
  pillLabel: {
    type: String,
  },
})
</script>

<template>
  <div class="card">
    <div class="left-side">
      <div class="left-side-content">
        <h2>{{ title }}</h2>
        <p>{{ text }}</p>
      </div>
    </div>
    
    <div class="right-side">
      <TCardImageSingle
        v-if="imageUrls && imageUrls.length === 1"
        :image-url="imageUrls[0]"
        :pill-label="pillLabel"
      />

      <TCardImageDouble
        v-if="imageUrls && imageUrls.length > 1"
        :image-urls="imageUrls"
        :pill-label="pillLabel"
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
  text-align: left;
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

p {
  line-height: 1.4;
}

.right-side {
  position: relative;
}

@media only screen and (max-width: 992px) {
  .card {
    height: auto;
    flex-direction: column;
    align-items: center;
  }

  .left-side {
    min-height: 15rem;
    width: 80%;
  }

  .right-side {
    width: 80%;
    height: 25rem;
  }

  .left-side-content {
    height: 100%;
  }
}

@media only screen and (max-width: 600px) {
  .left-side,
  .right-side {
    width: 100%;
  }

  .left-side-content {
    padding-left: 3rem;
    padding-right: 3rem;
  }
}
</style>