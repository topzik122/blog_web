<template>
    <div class="flex gap-2">
        <p>Находится в проекте:</p>
        <span class="font-bold">pages\post\[id].vue</span>
    </div>
    <div class="flex gap-2">
        <p>Адрес этой страницы:</p>
        <span class="font-bold">/post/{{ id }}</span>
    </div>
    <div>
        <h1 class="text-2xl my-2">{{ post.title }}</h1>
        <p class="text-sm opacity-50 my-2">Просмотров: {{ post.views }}</p>
        <p>{{ post.body }}</p>
        <ul class="flex gap-2">
            <li v-for="tag in post.tags" :key="tag"
            class="text-[brown] cursor-pointer">
                <NuxtLink to="">{{ tag }}</NuxtLink>
            </li>
        </ul>
    </div>
</template>

<script setup>
const { id } = useRoute().params;

const post = ref({})
const index = useIndexStore();

const fetch = async () => {
    try {
        // включаем loader
        index.loader = true;

        const res = await $fetch(`https://dummyjson.com/post/${id}`)

        return post.value = res
    } catch (error) {
        console.log(error);
    } finally {
        // выключаем loader
        index.loader = false;
    }
}

onMounted(() => fetch())
</script>