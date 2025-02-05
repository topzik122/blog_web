<template>
    <header class="bg-[brown] dark:bg-gray-800 transition-colors">
        <nav class="flex gap-2 text-white">
            <NuxtLink :class="{ 'bg-white text-[brown]': route.path == '/' }" to="/">Главная</NuxtLink>
            <NuxtLink :class="{ 'bg-white text-[brown]': route.path == '/blog' }" to="/blog">Блог</NuxtLink>
            <NuxtLink :class="{ 'bg-white text-[brown]': route.path == '/about' }" to="/about">О нас</NuxtLink>
            <NuxtLink :class="{ 'bg-white text-[brown]': route.path == '/contact' }" to="/contact">Контакты</NuxtLink>
        </nav>
    </header>
</template>

<script setup>
const route = useRoute()
</script>