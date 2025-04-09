<template>
    <h1 class="my-4 text-2xl text-blue-700 darl:blue-500 font-medium">О нас</h1>
    <div class="text-black dark:text-white">
        <section>
            <p class="mb-4">
                Мы - команда увлеченных кулинаров и гастрономов, которые любят делиться своими рецептами и кулинарными находками. Наша цель - вдохновить вас на создание вкусных и здоровых блюд, которые порадуют вас и ваших близких.
            </p>
            <p class="mb-4">
                В нашем блоге вы найдете разнообразные рецепты, советы по приготовлению, а также истории о том, как еда может объединять людей. Мы верим, что готовка - это не только процесс, но и искусство, которое требует любви и терпения.
            </p>
            <p class="mb-4">
                Присоединяйтесь к нам в этом увлекательном путешествии по миру кулинарии! Мы рады делиться с вами нашими знаниями и опытом, а также узнавать о ваших кулинарных приключениях.
            </p>
        </section>

        <section class="mt-10">
            <h2 class="text-3xl font-semibold mb-4">Наша команда</h2>
            <div class="grid grid-cols-1 text-black md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div class="bg-gray-200 p-4 rounded-lg shadow">
                    <h3 class="text-xl font-bold">Эрик</h3>
                    <p>играет в доту и лучше бы он не заходил.При виде его все убегают</p>
                </div>
                <div class="bg-gray-200 p-4 rounded-lg shadow">
                    <h3 class="text-xl font-bold">void spirit</h3>
                    <p>очень сильный воин использующий очень много разных скилов для атаки и защиты универсал </p>
                </div>
                <div class="bg-gray-200 p-4 rounded-lg shadow">
                    <h3 class="text-xl font-bold">invoker</h3>
                    <p>Главный по касту скилов,расскажет про каждый скил и их работу </p>
                </div>
            </div>
        </section>
    </div>
</template>

<script setup>
const route = useRoute()
useHead({
    title: 'О нас | Гимназия №76'
})
</script>