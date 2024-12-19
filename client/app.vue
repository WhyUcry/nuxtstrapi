<template>
  <NuxtLoadingIndicator throttle="0" />
  <Navbar />
  <NuxtPage />
  <Up />
  <Footer />
</template>

<script setup>
  // const base_url = 'https://9ad68bbb32a5.vps.myjino.ru'
  const { id } = useRoute().params
  // const api = await $fetch('https://9ad68bbb32a5.vps.myjino.ru/api/posts?populate=*')
  // const posts = api.data.posts
  // const posts = api.data


  const base = 'https://9ad68bbb32a5.vps.myjino.ru' 
  const api = await $fetch(`${base}/api/config?populate=*`)
  const config = api.data

  useHead({
    title: config.title,
    meta: [
      { name: 'description', content: config.desc },
      { name: 'keywords', content: config.keywords },
    ],
    bodyAttrs: {
      class: 'container mx-auto bg-white dark:bg-gray-900'
    },
    head: {
      script: [
        { src: 'https://yastatic.net/share2/share.js', async: true, defer: true },
        { src: 'https://cdn.jsdelivr.net/npm/flowbite@2.5.2/dist/flowbite.min.css', async: true, defer: true }
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
