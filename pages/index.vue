<template>
  <h1>Главная страница</h1>
  <p>path: {{ route.path }}</p>
</template>


<script setup>
const route = useRoute()
useHead({
    title: 'Главная | Академия ТОП',
    bodyAttrs: {
      class: 'bg-teal-600'
    }
})
</script>