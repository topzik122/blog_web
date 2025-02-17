<template>
    <div class="max-w-3xl mx-auto text-black dark:text-white">
        <h1 class="text-4xl font-medium my-2">{{ post.title }}</h1>
        <p class="opacity-50 my-1.5">Опубликовано: {{ convertDatetime(post.publishedAt) }}</p>
        <div class="markdown my-1.5" v-html="body"></div>
    </div>
</template>

<script setup>

function convertDatetime(isoDatetime) {
    // Создаем объект Date из строки
    const date = new Date(isoDatetime);

    // Определяем массив с русскими названиями месяцев
    const months = [
        "янв", "фев", "мар", "апр", "май", "июн",
        "июл", "авг", "сен", "окт", "ноя", "дек"
    ];

    // Получаем компоненты даты
    const day = String(date.getUTCDate()).padStart(2, '0');
    const month = months[date.getUTCMonth()];
    const year = date.getUTCFullYear();
    const hours = String(date.getUTCHours()).padStart(2, '0');
    const minutes = String(date.getUTCMinutes()).padStart(2, '0');

    // Форматируем строку
    return `${day} ${month} ${year} в ${hours}:${minutes}`;
}

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