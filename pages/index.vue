<template>
  <h1 class="my-4 text-2xl text-blue-700 darl:blue-500 font-medium">Главная страница</h1>
</template>

<script setup>
const index = useIndexStore();
// const search = ref('')

// watch(index.search, async (newSearch) => {
//   search.value = newSearch
// })

useHead({
  title: 'Главная | Академия ТОП',
})
</script>