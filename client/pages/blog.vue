<template>
    <main>
        <h2 class="text-2xl my-4 dark:text-white opacity-75">Блог</h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 2xl:grid-cols-4 gap-4 mb-4">
            <article v-for="post in displayedPosts" :key="post.id" class="max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
                <NuxtLink class="block overflow-hidden" :to="'/post/' + post.documentId">
                    <img class="lg:h-48 md:h-36 w-full object-cover object-center" :src="base_url + post.img.url" :alt="post.img.alternativeText" />
                </NuxtLink>
                <div class="p-5">
                    <NuxtLink :to="'/post/' + post.documentId">
                        <h5 class="title-font text-lg font-medium text-gray-900 mb-3">{{ post.title }}</h5>
                    </NuxtLink>
                    <p class="title-font text-lg font-medium text-gray-900 mb-3">{{ post.desc }}</p>
                    <NuxtLink :to="'/post/' + post.documentId" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                        Подробнее
                        <svg class="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
                        </svg>
                    </NuxtLink>
                </div>
            </article>
        </div>
        <button v-if="!(displayedPosts.length === posts.length)" @click="loadMore" type="button" class="w-full text-blue-700 hover:text-white border border-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center me-2 mb-2 dark:border-blue-500 dark:text-blue-500 dark:hover:text-white dark:hover:bg-blue-500 dark:focus:ring-blue-800">Смотреть еще</button>
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

const base_url = "https://9ad68bbb32a5.vps.myjino.ru";
const posts = ref([]); // Инициализируем posts как реактивную переменную
const displayedPosts = ref([]); // Инициализируем displayedPosts как реактивную переменную
const error = ref(null);

onMounted(async () => {
    try {
        const api = await $fetch(`${base_url}/api/posts?populate=*`);
        posts.value = api.data; // Присваиваем данные в posts
        displayedPosts.value = posts.value.slice(0, 12); // Отображаем первые 12 статей
    } catch (err) {
        console.error('Ошибка при загрузке постов:', err);
        error.value = 'Не удалось загрузить посты. Пожалуйста, попробуйте позже.';
    }
});

const loadMore = () => {
    const nextPosts = posts.value.slice(displayedPosts.value.length, displayedPosts.value.length + 4);
    displayedPosts.value.push(...nextPosts); // Добавляем новые посты в displayedPosts
};
</script>