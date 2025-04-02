<script setup>
import TButton from '../ui/TButton.vue';
import TCard from '../ui/TCard.vue';
import TPost from '../ui/TPost.vue';
</script>

<template>
  <section class="body-section">
    <TCard
      title="This is a card lorem ispum dolor sit"
      text="Lorem ipsum dolor sit amet consectetur. Sed pulvinar odio velit fermentum etiam consectetur pretium fringilla metus."
      background-color="#fff"
      :image-urls="['https://tf-frontend.netlify.app/images/v1/card_img.png']"
    />

    <div class="blog">
      <h2>Lorem Ipsum Dolor Sit Amet</h2>

      <div class="posts-scroller">
        <div class="posts">
          <TPost date="22-02-22" type="Type A" title="This is the title of the journal post." image-url="https://tf-frontend.netlify.app/images/v1/post_1.png"/>
          <TPost date="22-02-22" type="Type B" title="This is the title of the journal post." image-url="https://tf-frontend.netlify.app/images/v1/post_1.png"/>
          <TPost date="22-02-22" type="Type A" title="This is the title of the journal post." image-url="https://tf-frontend.netlify.app/images/v1/post_1.png"/>
          <TPost date="22-02-22" type="Type A" title="This is the title of the journal post." image-url="https://tf-frontend.netlify.app/images/v1/post_1.png"/>
        </div>
      </div>

      <TButton label="Our Blog"/>
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