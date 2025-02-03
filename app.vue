<template>
  <button @click="toggleTheme('dark')" class="cursor-pointer">Темная тема</button>
  <button @click="toggleTheme('')" class="cursor-pointer">Светлая тема</button>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

<script setup>
const dark = ref('')

const toggleTheme = (theme) => {
  dark.value = theme
  console.log(dark.value);
  
}

watch(dark, (newValue) => {
  useHead({
    title: 'Академия ТОП',
    htmlAttrs: {
      class: newValue
    }
  })
})
</script>