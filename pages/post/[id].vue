<template>
    <div class="flex gap-2">
        <p>Находится в проекте:</p>
        <span class="font-bold">pages\post\[documentId].vue</span>
    </div>
    <div class="flex gap-2">
        <p>Адрес этой страницы:</p>
        <span class="font-bold">/post/{{ id }}</span>
    </div>
    <div>
        <h1 class="text-4xl font-medium my-2">{{ post.title }}</h1>
        <div class="markdown" v-html="body"></div>
    </div>
</template>

<script setup>
const { id } = useRoute().params;

const post = ref({})
const index = useIndexStore();

import markdownit from 'markdown-it'
const md = markdownit()
const body = ref()
watch(post, (newPost) => {
    body.value = md.render(newPost.body);
})

const fetch = async () => {
    try {
        // включаем loader
        index.loader = true;

        const res = await $fetch(`http://localhost:1337/api/posts/${id}?populate=*`)

        return post.value = res.data
    } catch (error) {
        console.log(error);
    } finally {
        // выключаем loader
        index.loader = false;
    }
}

onMounted(() => fetch())
</script>