<template>
    <main>
        <h2 class="text-2xl my-4 dark:text-white opacity-75">Главная страница</h2>

        <ClientOnly>
            <swiper-container ref="containerRef" class="h-48">
                <swiper-slide
                    v-for="(slide, idx) in slides"
                    :key="idx"
                    style="background-color: rgb(32, 233, 70); color: white;">

                    
                    Слайд {{ idx + 1 }}
                </swiper-slide>
            </swiper-container>
        </ClientOnly>

        <!-- Go back one slide -->
        <button @click="swiper.prev()">
            Prev
        </button>
        <!-- Go forward one slide -->
        <button @click="swiper.next()">
            Next
        </button>

    </main>
</template>

<script setup>
    // Create 10 slides
    const containerRef = ref(null)
    const slides = ref(Array.from({ length: 10 }))

    const swiper = useSwiper(containerRef)

    onMounted(() => {
    // Access Swiper instance
    // Read more about Swiper instance: https://swiperjs.com/swiper-api#methods--properties
    console.log(swiper.instance)
    })
</script>