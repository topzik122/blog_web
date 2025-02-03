<template>
    <div class="max-w-5xl mx-auto">
        <h1 class=" font-bold text-2xl">{{ post.title }}</h1>
        <p class="text-black/50">Просмотры: {{ post.views }}</p>
        <p>{{ post.body }}</p>
    </div>
</template>

<script setup>
const { id } = useRoute().params;

const post = ref({})

const fetch = async () => {
    try {
        const res = await $fetch(`https://dummyjson.com/posts/${id}`)

        return post.value = res
    } catch (error) {
        console.log(error);
    }
}

onMounted(() => fetch())
</script>