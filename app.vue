<template>
  <AppLoader v-if="loader.loader" />
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

<script setup>
const loader = useIndexStore();
</script>