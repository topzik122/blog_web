<template>
    <h1>О нас</h1>
    <p>path: {{ route.path }}</p>
</template>


<script setup>
const route = useRoute()
useHead({
    title: 'О нас | Академия ТОП'
})
</script>