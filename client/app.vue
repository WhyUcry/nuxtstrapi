<template>
  <!-- <Navbar />
  <h1 class="text-2xl ml-96 mt-8">Посты</h1>
  <hr style="
    width: 1250px;
    margin: 0 auto;
    margin-top: 20px;
  ">
    <div class="post" v-for="post in posts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.content }}</p>
      <img :src="base_url+post.img.url" :alt="post.img.alternativeText" width="300">
    </div>

    <div class="post1" v-for="post1 in post1s" :key="post1.id">
      <h2>{{ post1.title }}</h2>
      <p>{{ post1.content }}</p>
      <img :src="base_url+post1.img.url" :alt="post1.img.alternativeText" width="300">
    </div>


  <div class="flex justify-center	mt-16">
    <AllPosts />
  </div>

  <Footer /> -->




  <NuxtLoadingIndicator throttle="0" />
  <Navbar />
  <NuxtPage />
  <!-- <Up /> -->
  <Footer />
</template>

<script setup>
  // const base_url = 'http://localhost:1337'
  // const { id } = useRoute().params
  // const api = await $fetch('http://localhost:1337/api/categories/${id}?populate=posts.img&populate=posts.categories')
  // const api = await $fetch('http://localhost:1337/api/posts?populate=*')
  // const posts = api.data.posts
  // const posts = api.data



  const base = 'http://localhost:1337' 
  const api = await $fetch(`${base}/api/posts?populate=*`)
  const config = api.data

  useHead({
    title: config.title,
    meta: [
      { name: 'description', content: config.desc },
      { name: 'keywords', content: config.keywords },
    ],
    link: [
      { rel: 'icon', type: 'image/x-icon', href: base+config.favicon.url },
    ],
    bodyAttrs: {
      class: 'container mx-auto bg-white dark:bg-gray-900'
    },
    head: {
      script: [
        { src: 'https://yastatic.net/share2/share.js', async: true, defer: true }
      ]
    }
  })
</script>

<style scoped>
  .posts {
    display: flex;
    flex-direction: column;
  }
</style>
