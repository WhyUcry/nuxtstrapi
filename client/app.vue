<template>
  <div>
    <Navbar />
    <h1 class="text-2xl ml-96 mt-8">Посты</h1>
      <!-- <div class="post" v-for="post in posts" :key="post.id">
        <h2>{{ post.title }}</h2>
        <p>{{ post.content }}</p>
        <img :src="base_url+post.img.url" :alt="post.img.alternativeText" width="300">
      </div> -->

      <!-- <div class="post1" v-for="post1 in post1s" :key="post1.id">
        <h2>{{ post1.title }}</h2>
        <p>{{ post1.content }}</p>
        <img :src="base_url+post1.img.url" :alt="post1.img.alternativeText" width="300">
      </div> -->


    <div class="flex justify-center	mt-16">
      <AllPosts />
    </div>

    <Footer />
  </div>
</template>

<script setup>
  const base_url = 'http://localhost:1337'
  const { id } = useRoute().params
  // const api = await $fetch('http://localhost:1337/api/categories/${id}?populate=posts.img&populate=posts.categories')
  const api = await $fetch('http://localhost:1337/api/posts?populate=*')
  // const posts = api.data.posts
  const posts = api.data
</script>

<style scoped>
  .posts {
    display: flex;
    flex-direction: column;
  }
</style>
