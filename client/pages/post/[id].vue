<template>
    <main class="w-full lg:px-40">
        <div class="ns_post" v-if="post">
            <div class="h-96 bg-[length:100%_600px] rounded-2xl my-4 bg-fixed" :style="'background-image: url(' + base_url + post.img.url + ')'"></div>
            <h1 class="relative text-4xl">{{ post.title }} <Share /></h1>
            <p>{{ post.content }}</p>
            <div v-html="mark"></div>
        </div>
        <div v-else-if="error">
            <p>Произошла ошибка: {{ error }}</p>
        </div>
        <div v-else>
            <p>Загрузка...</p>
        </div>
    </main>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import MarkdownIt from "markdown-it";

const markdown = new MarkdownIt();
const { id } = useRoute().params;
const base_url = 'https://9ad68bbb32a5.vps.myjino.ru';
const post = ref(null);
const error = ref(null);

onMounted(async () => {
    try {
        const api = await $fetch(`https://9ad68bbb32a5.vps.myjino.ru/api/posts/${id}?populate=*`);
        post.value = api.data;
    } catch (err) {
        console.error('Ошибка при загрузке поста:', err);
        error.value = 'Не удалось загрузить пост. Пожалуйста, попробуйте позже.';
    }
});
</script>