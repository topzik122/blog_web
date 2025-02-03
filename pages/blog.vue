<template>
    <h1>Блог</h1>
    <!-- {{ posts }} -->
    <div class="grid grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">
        <!-- <article v-for="post in posts" :key="post.id"
            class="bg-[brown] text-[wheat] p-2">
            <h3>{{ post.title }}</h3>
            <ul>
                <li v-for="tag in post.tags" :key="tag">
                    {{ tag }}
                </li>
            </ul>
            <p>Просмотров: {{ post.views }}</p>
            <NuxtLink to="">Читать статью</NuxtLink>
        </article> -->
        <article class="mx-auto max-w-md overflow-hidden rounded-xl bg-white shadow-md md:max-w-2xl"
            v-for="post in posts" :key="post.id">
            <div class="md:flex">
                <div class="md:shrink-0">
                    <img class="h-48 w-full object-cover md:h-full md:w-48"
                        src="https://images.unsplash.com/photo-1637734433731-621aca1c8cb6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=404&q=80"
                        alt="Modern building architecture" />
                </div>
                <div class="p-8">
                    <div class="flex gap-2">
                        <div class="text-sm font-semibold tracking-wide text-indigo-500 uppercase"
                            v-for="tag in post.tags" :key="tag">
                            {{ tag }}
                        </div>
                    </div>
                    <NuxtLink :to="'/post/'+post.id" class="mt-1 block text-lg leading-tight font-medium text-black hover:underline">
                        {{ post.title }}
                    </NuxtLink>
                </div>
            </div>
        </article>
    </div>
</template>

<script setup>
const posts = ref([])

const fetch = async () => {
    try {
        const res = await $fetch('https://dummyjson.com/posts')

        return posts.value = res.posts
    } catch (error) {
        console.log(error);
    }
}

onMounted(() => fetch())
</script>