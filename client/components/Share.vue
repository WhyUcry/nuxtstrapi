<template>
    <div class="absolute -left-20 top-2 ya-share2" data-curtain data-services="messenger,vkontakte,odnoklassniki,telegram,viber,whatsapp"></div>
</template>

<script setup>
import('https://yastatic.net/share2/share.js')

useHead({
    head: {
        script: [
            {
                src: 'https://yastatic.net/share2/share.js',
                async: true,
                defer: true
            }
        ]
    }
})

const loadShareScript = () => {
  useHead({
      script: [
          {
            src: 'https://yastatic.net/share2/share.js',
            async: true,
            defer: true
          }
      ]
  })
}

onMounted(loadShareScript())
</script>

<style>
.ya-share2__list {
    display: flex !important;
    flex-flow: column !important;
}

.ya-share2__list:hover li {
    filter: grayscale(1);
}

.ya-share2__list li:hover {
    filter: grayscale(0);
}
</style>