<template>
    <header class="flex justify-between relative py-3 px-4 bg-gradient-to-r from-amber-600 via-amber-700 to-amber-800 text-amber-100">
        <p>Логотип</p>
        <!-- десктопное меню -->
        <nav class="hidden md:block">
            <ul class="flex items-center gap-2">
                <li>
                    <NuxtLink class="py-2 px-4 hover:bg-amber-600/50 transition-colors rounded-lg"
                        to="/">Главная</NuxtLink>
                </li>
                <li>
                    <NuxtLink class="py-2 px-4 hover:bg-amber-600/50 transition-colors rounded-lg"
                        to="/about">О нас</NuxtLink>
                </li>
                <li>
                    <NuxtLink class="py-2 px-4 hover:bg-amber-600/50 transition-colors rounded-lg"
                        to="/contact">Контакты</NuxtLink>
                </li>
            </ul>
        </nav>
        <!-- мобильное меню -->
        <button @click="mobileMenu = !mobileMenu" class="block md:hidden size-6">
            <svg v-if="!mobileMenu" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M18 18V20H6V18H18ZM21 11V13H3V11H21ZM18 4V6H6V4H18Z"></path></svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor"><path d="M10.5859 12L2.79297 4.20706L4.20718 2.79285L12.0001 10.5857L19.793 2.79285L21.2072 4.20706L13.4143 12L21.2072 19.7928L19.793 21.2071L12.0001 13.4142L4.20718 21.2071L2.79297 19.7928L10.5859 12Z"></path></svg>
        </button>
        <nav v-if="mobileMenu" class="absolute top-12 left-0 w-full">
            <ul class="bg-gray-100 text-black">
                <li>
                    <NuxtLink @click="mobileMenu = !mobileMenu" class="block py-3 px-2 active:bg-amber-200" to="/">Главная</NuxtLink>
                </li>
                <li>
                    <NuxtLink @click="mobileMenu = !mobileMenu" class="block py-3 px-2 active:bg-amber-200" to="/about">О нас</NuxtLink>
                </li>
                <li>
                    <NuxtLink @click="mobileMenu = !mobileMenu" class="block py-3 px-2 active:bg-amber-200" to="/contact">Контакты</NuxtLink>
                </li>
            </ul>
        </nav>
    </header>
</template>

<script setup>
const mobileMenu = ref(false)
</script>