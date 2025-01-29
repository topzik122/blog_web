<template>
  <div class="flex flex-col h-full">
    <AppHeader />
    <main class="flex-auto">
      <NuxtPage />
    </main>
    <AppFooter />
  </div>
</template>

<script setup>
useHead({
  htmlAttrs: {
    class: 'flex flex-col h-full',
  },
  bodyAttrs: {
    class: 'flex flex-col h-full',
  },
})

useSeoMeta({
  title: 'Наш первый сайт на Nuxt.js',
  ogTitle: 'Наш первый сайт на Nuxt.js',
  description: 'This is my amazing site, let me tell you all about it.',
  ogDescription: 'This is my amazing site, let me tell you all about it.',
  ogImage: 'https://example.com/image.png',
})
</script>
