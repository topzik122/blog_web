<template>
    <h1 class="my-4 text-2xl text-blue-700 darl:blue-500 font-medium">Блог</h1>
    <div class="grid grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">
        <article v-for="post in posts" :key="post.id"
                class="max-w-sm bg-white border border-gray-200 rounded-lg shadow-sm dark:bg-gray-800 dark:border-gray-700">
            <NuxtLink :to="`/post/${post.id}`" href="#">
                <img class="rounded-t-lg" src="https://flowbite.com/docs/images/blog/image-1.jpg" alt="" />
            </NuxtLink>
            <div class="p-5">
                <NuxtLink :to="`/post/${post.id}`" href="#">
                    <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ post.title }}</h5>
                </NuxtLink>
                <ul class="flex gap-1 mb-3 font-normal text-gray-700 dark:text-gray-400">
                    <li v-for="tag in post.tags" :key="tag"
                     class="text-red-400 p-2 underline hover:bg-[brown]/80 hover:text-white cursor-pointer rounded-lg">
                        {{ tag }}
                    </li>
                </ul>
                <NuxtLink :to="`/post/${post.id}`" href="#" class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-[brown]/80 rounded-lg hover:bg-[brown] focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                    Подробнее
                    <svg class="rtl:rotate-180 w-3.5 h-3.5 ms-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 5h12m0 0L9 1m4 4L9 9"/>
                    </svg>
                </NuxtLink>
            </div>
        </article>
    </div>
</template>

<script setup>
const posts = ref([])
const index = useIndexStore();

const fetch = async () => {
    try {
        // включаем loader
        index.loader = true;

        const res = await $fetch('https://dummyjson.com/posts')

        return posts.value = res.posts
    } catch (error) {
        console.log(error);
    } finally {
        // выключаем loader
        index.loader = false;
    }
}

onMounted(() => fetch())
</script>