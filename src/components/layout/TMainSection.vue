<script setup>
import { inject } from 'vue';
import TButton from '../ui/TButton.vue';
import TCard from '../ui/TCard.vue';
import TPost from '../ui/TPost.vue';

const introCardData = inject('introCardData')
const blogData = inject('blogData')
</script>

<template>
  <section class="body-section">
    <TCard
      :title="introCardData?.title"
      :text="introCardData?.subtitle"
      background-color="#fff"
      :image-urls="[introCardData?.image]"
      :pill-label="introCardData?.pill"
    />

    <div class="blog">
      <h2>{{blogData?.title}}</h2>

      <div class="posts-scroller">
        <div class="posts">
          <template v-for="(post, index) in blogData?.posts" >
            <TPost 
              :date="post?.date" 
              :type="post?.type" 
              :title="post?.title" 
              :image-url="post?.image"
            />
          </template>
        </div>
      </div>

      <TButton :label="blogData?.button_label" :link="blogData?.button_link"/>
    </div>
  </section>
</template>

<style scoped>
section {
  padding: 7.5rem;
  gap: 6rem;
  background-color: var(--background-color-dark);
  text-align: center;
  overflow: hidden;
}

.blog {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4rem;
  width: 100%;
}

.posts-scroller {
  display: block;
  width: 85%;
  max-width: 75rem;
  overflow-x: auto;
}

.posts {
  display: flex;
  justify-content: space-between;
  width: 75rem;
  height: 32.5rem;
}
</style>