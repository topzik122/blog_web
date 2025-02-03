<template>
    <h1>Контакты</h1>
    <ul>
        <li>Номер: +7 (993) 307-98-29</li>
        <li>Почта: oleg@nastyle.pro</li>
    </ul>
    <p>path: {{ route.path }}</p>
</template>


<script setup>
const route = useRoute()
useHead({
    title: 'Контакты | Академия ТОП'
})
</script>