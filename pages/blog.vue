<template>
    <h1 class="text-2xl font-medium">Блог</h1>
    <div class="grid grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">
        <article v-for="post in posts" :key="post.id"
            class="bg-[brown] text-[wheat] p-2">
            <h3>{{ post.title }}</h3>
            <ul class="flex gap-2 bg-white text-[brown] w-max">
                <li v-for="tag in post.tags" :key="tag">
                    {{ tag }}
                </li>
            </ul>
            <p>Просмотров: {{ post.views }}</p>
            <NuxtLink :to="`/post/${post.id}`">Читать статью</NuxtLink>
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