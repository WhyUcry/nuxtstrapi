<template>
  <div>
    <h1>Посты</h1>
      <div class="posts" v-for="post in posts" :key="post.id">
        <h2>{{ post.title }}</h2>
        <p>{{ post.content }}</p>
        <img :src="base_url+post.img.url" :alt="post.img.alternativeText" width="300">
      </div>
  </div>
</template>

<script setup>
  const dataTwice = await $fetch('http://localhost:1337/api/posts?populate=*')
  const posts = dataTwice.data
  const base_url = 'http://localhost:1337'
</script>

<style scoped>
  .posts {
    display: flex;
    flex-direction: column;
  }
</style>

<!-- <script>
export default {
  data() {
    return {
      posts: [],
      error: null,
    }
  },
  async fetch() {
    try {
      const response = await fetch('http://localhost:1337/api/posts', {
        method: 'GET',
        headers: {
          'Content-Type': 'application/json',
        },
      });

      if (!response.ok) {
        throw new Error('Ошибка при загрузке данных');
      }

      const data = await response.json();
      this.posts = data;
    } catch (error) {
      this.error = error.message;
    }
  },
}
</script> -->
