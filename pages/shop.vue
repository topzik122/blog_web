<template>
    <h1 class="my-4 text-2xl text-cyan-700 darl:blue-500 font-medium">Магазин</h1>
    <!-- список продуктов -->
    <div class="bg-white">
  <div class="mx-auto max-w-2xl px-4 py-16 sm:px-6 sm:py-24 lg:max-w-7xl lg:px-8">
    <h2 class="text-2xl font-bold tracking-tight text-gray-900">Customers also purchased</h2>

    <div class="mt-6 grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8">
      <div v-for="(post, index) in posts" :key="post.id" class="group relative">
        <img :src="'https://static.dublecode.ru' + post.cover.url" alt="Product image" class="aspect-square w-full rounded-md bg-gray-200 object-cover group-hover:opacity-75 lg:aspect-auto lg:h-80">
        <div class="mt-4 flex justify-between">
          <div>
            <h3 class="text-sm text-gray-700">
              <a href="#" @click.prevent="selectPost(post)">
                <span aria-hidden="true" class="absolute inset-0"></span>
                {{ post.title }}
              </a>
            </h3>
            <p class="mt-1 text-sm text-gray-500">{{ post.color }}</p>
          </div>
          <p class="text-sm font-medium text-gray-900">{{ post.price }}</p>
        </div>
      </div>
    </div>
  </div>
</div>

    <div v-if="isModalOpen && selectedPost" class="relative z-10" role="dialog" aria-modal="true">
        <!--
            Background backdrop, show/hide based on modal state.

            Entering: "ease-out duration-300"
            From: "opacity-0"
            To: "opacity-100"
            Leaving: "ease-in duration-200"
            From: "opacity-100"
            To: "opacity-0"
        -->
        <div class="fixed inset-0 hidden bg-gray-500/75 transition-opacity md:block" aria-hidden="true"></div>

        <div class="fixed inset-0 z-10 w-screen overflow-y-auto">
            <div class="flex min-h-full items-stretch justify-center text-center md:items-center md:px-2 lg:px-4">
            <!--
                Modal panel, show/hide based on modal state.

                Entering: "ease-out duration-300"
                From: "opacity-0 translate-y-4 md:translate-y-0 md:scale-95"
                To: "opacity-100 translate-y-0 md:scale-100"
                Leaving: "ease-in duration-200"
                From: "opacity-100 translate-y-0 md:scale-100"
                To: "opacity-0 translate-y-4 md:translate-y-0 md:scale-95"
            -->
            <div class="flex w-full transform text-left text-base transition md:my-8 md:max-w-2xl md:px-4 lg:max-w-4xl">
                <div class="relative flex w-full items-center overflow-hidden bg-white px-4 pb-8 pt-14 shadow-2xl sm:px-6 sm:pt-8 md:p-6 lg:p-8">
                <button type="button" @click="closeModal" class="absolute right-4 top-4 text-gray-400 hover:text-gray-500 sm:right-6 sm:top-8 md:right-6 md:top-6 lg:right-8 lg:top-8">
                    <span class="sr-only">Закрыть</span>
                    <svg class="size-6" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true" data-slot="icon">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
                    </svg>
                </button>

                <div class="grid w-full grid-cols-1 items-start gap-x-6 gap-y-8 sm:grid-cols-12 lg:gap-x-8">
                    <img :src="'https://static.dublecode.ru' + selectedPost.cover.url" alt="Product image" class="aspect-[2/3] w-full rounded-lg bg-gray-100 object-cover sm:col-span-4 lg:col-span-5">
                    <div class="sm:col-span-8 lg:col-span-7">
                    <h2 class="text-2xl font-bold text-gray-900 sm:pr-12">{{ selectedPost.title }}</h2>

                    <section aria-labelledby="information-heading" class="mt-2">
                        <h3 id="information-heading" class="sr-only">Product information</h3>

                        <p class="text-2xl text-gray-900">{{ selectedPost.price }}</p>

                        <!-- Reviews -->
                        <div class="mt-6">
                        <h4 class="sr-only">Reviews</h4>
                        <div class="flex items-center">
                            <div class="flex items-center">
                            <!-- Active: "text-gray-900", Default: "text-gray-200" -->
                            <svg class="size-5 shrink-0 text-gray-900" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true" data-slot="icon">
                                <path fill-rule="evenodd" d="M10.868 2.884c-.321-.772-1.415-.772-1.736 0l-1.83 4.401-4.753.381c-.833.067-1.171 1.107-.536 1.651l3.62 3.102-1.106 4.637c-.194.813.691 1.456 1.405 1.02L10 15.591l4.069 2.485c.713.436 1.598-.207 1.404-1.02l-1.106-4.637 3.62-3.102c.635-.544.297-1.584-.536-1.65l-4.752-.382-1.831-4.401Z" clip-rule="evenodd" />
                            </svg>
                            <svg class="size-5 shrink-0 text-gray-900" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true" data-slot="icon">
                                <path fill-rule="evenodd" d="M10.868 2.884c-.321-.772-1.415-.772-1.736 0l-1.83 4.401-4.753.381c-.833.067-1.171 1.107-.536 1.651l3.62 3.102-1.106 4.637c-.194.813.691 1.456 1.405 1.02L10 15.591l4.069 2.485c.713.436 1.598-.207 1.404-1.02l-1.106-4.637 3.62-3.102c.635-.544.297-1.584-.536-1.65l-4.752-.382-1.831-4.401Z" clip-rule="evenodd" />
                            </svg>
                            <svg class="size-5 shrink-0 text-gray-900" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true" data-slot="icon">
                                <path fill-rule="evenodd" d="M10.868 2.884c-.321-.772-1.415-.772-1.736 0l-1.83 4.401-4.753.381c-.833.067-1.171 1.107-.536 1.651l3.62 3.102-1.106 4.637c-.194.813.691 1.456 1.405 1.02L10 15.591l4.069 2.485c.713.436 1.598-.207 1.404-1.02l-1.106-4.637 3.62-3.102c.635-.544.297-1.584-.536-1.65l-4.752-.382-1.831-4.401Z" clip-rule="evenodd" />
                            </svg>
                            <svg class="size-5 shrink-0 text-gray-900" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true" data-slot="icon">
                                <path fill-rule="evenodd" d="M10.868 2.884c-.321-.772-1.415-.772-1.736 0l-1.83 4.401-4.753.381c-.833.067-1.171 1.107-.536 1.651l3.62 3.102-1.106 4.637c-.194.813.691 1.456 1.405 1.02L10 15.591l4.069 2.485c.713.436 1.598-.207 1.404-1.02l-1.106-4.637 3.62-3.102c.635-.544.297-1.584-.536-1.65l-4.752-.382-1.831-4.401Z" clip-rule="evenodd" />
                            </svg>
                            <svg class="size-5 shrink-0 text-gray-200" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true" data-slot="icon">
                                <path fill-rule="evenodd" d="M10.868 2.884c-.321-.772-1.415-.772-1.736 0l-1.83 4.401-4.753.381c-.833.067-1.171 1.107-.536 1.651l3.62 3.102-1.106 4.637c-.194.813.691 1.456 1.405 1.02L10 15.591l4.069 2.485c.713.436 1.598-.207 1.404-1.02l-1.106-4.637 3.62-3.102c.635-.544.297-1.584-.536-1.65l-4.752-.382-1.831-4.401Z" clip-rule="evenodd" />
                            </svg>
                            </div>
                            <p class="sr-only">3.9 out of 5 stars</p>
                            <a href="#" class="ml-3 text-sm font-medium text-indigo-600 hover:text-indigo-500">117 reviews</a>
                        </div>
                        </div>
                    </section>

                    <section aria-labelledby="options-heading" class="mt-10">
                        <h3 id="options-heading" class="sr-only">Product options</h3>

                        <form>
                        <!-- Colors -->
                        <fieldset aria-label="Choose a color">
                            <legend class="text-sm font-medium text-gray-900">Color</legend>

                            <div class="mt-4 flex items-center gap-x-3">
                            <!-- Active and Checked: "ring ring-offset-1" -->
                            <label aria-label="White" class="relative -m-0.5 flex cursor-pointer items-center justify-center rounded-full p-0.5 ring-gray-400 focus:outline-none">
                                <input type="radio" name="color-choice" value="White" class="sr-only">
                                <span aria-hidden="true" class="size-8 rounded-full border border-black/10 bg-white"></span>
                            </label>
                            <!-- Active and Checked: "ring ring-offset-1" -->
                            <label aria-label="Gray" class="relative -m-0.5 flex cursor-pointer items-center justify-center rounded-full p-0.5 ring-gray-400 focus:outline-none">
                                <input type="radio" name="color-choice" value="Gray" class="sr-only">
                                <span aria-hidden="true" class="size-8 rounded-full border border-black/10 bg-gray-200"></span>
                            </label>
                            <!-- Active and Checked: "ring ring-offset-1" -->
                            <label aria-label="Black" class="relative -m-0.5 flex cursor-pointer items-center justify-center rounded-full p-0.5 ring-gray-900 focus:outline-none">
                                <input type="radio" name="color-choice" value="Black" class="sr-only">
                                <span aria-hidden="true" class="size-8 rounded-full border border-black/10 bg-gray-900"></span>
                            </label>
                            </div>
                        </fieldset>

                        <!-- Sizes -->
                        <fieldset class="mt-10" aria-label="Choose a size">
                            <div class="flex items-center justify-between">
                            <div class="text-sm font-medium text-gray-900">Size</div>
                            <a href="#" class="text-sm font-medium text-indigo-600 hover:text-indigo-500">Size guide</a>
                            </div>

                            <div class="mt-4 grid grid-cols-4 gap-4">
                            <!-- Active: "ring-2 ring-indigo-500" -->
                            <label class="group relative flex cursor-pointer items-center justify-center rounded-md border bg-white px-4 py-3 text-sm font-medium uppercase text-gray-900 shadow-sm hover:bg-gray-50 focus:outline-none sm:flex-1">
                                <input type="radio" name="size-choice" value="XXS" class="sr-only">
                                <span>XXS</span>
                                <!--
                                Active: "border", Not Active: "border-2"
                                Checked: "border-indigo-500", Not Checked: "border-transparent"
                                -->
                                <span class="pointer-events-none absolute -inset-px rounded-md" aria-hidden="true"></span>
                            </label>
                            <!-- Active: "ring-2 ring-indigo-500" -->
                            <label class="group relative flex cursor-pointer items-center justify-center rounded-md border bg-white px-4 py-3 text-sm font-medium uppercase text-gray-900 shadow-sm hover:bg-gray-50 focus:outline-none sm:flex-1">
                                <input type="radio" name="size-choice" value="XS" class="sr-only">
                                <span>XS</span>
                                <!--
                                Active: "border", Not Active: "border-2"
                                Checked: "border-indigo-500", Not Checked: "border-transparent"
                                -->
                                <span class="pointer-events-none absolute -inset-px rounded-md" aria-hidden="true"></span>
                            </label>
                            <!-- Active: "ring-2 ring-indigo-500" -->
                            <label class="group relative flex cursor-pointer items-center justify-center rounded-md border bg-white px-4 py-3 text-sm font-medium uppercase text-gray-900 shadow-sm hover:bg-gray-50 focus:outline-none sm:flex-1">
                                <input type="radio" name="size-choice" value="S" class="sr-only">
                                <span>S</span>
                                <!--
                                Active: "border", Not Active: "border-2"
                                Checked: "border-indigo-500", Not Checked: "border-transparent"
                                -->
                                <span class="pointer-events-none absolute -inset-px rounded-md" aria-hidden="true"></span>
                            </label>
                            <!-- Active: "ring-2 ring-indigo-500" -->
                            <label class="group relative flex cursor-pointer items-center justify-center rounded-md border bg-white px-4 py-3 text-sm font-medium uppercase text-gray-900 shadow-sm hover:bg-gray-50 focus:outline-none sm:flex-1">
                                <input type="radio" name="size-choice" value="M" class="sr-only">
                                <span>M</span>
                                <!--
                                Active: "border", Not Active: "border-2"
                                Checked: "border-indigo-500", Not Checked: "border-transparent"
                                -->
                                <span class="pointer-events-none absolute -inset-px rounded-md" aria-hidden="true"></span>
                            </label>
                            <!-- Active: "ring-2 ring-indigo-500" -->
                            <label class="group relative flex cursor-pointer items-center justify-center rounded-md border bg-white px-4 py-3 text-sm font-medium uppercase text-gray-900 shadow-sm hover:bg-gray-50 focus:outline-none sm:flex-1">
                                <input type="radio" name="size-choice" value="L" class="sr-only">
                                <span>L</span>
                                <!--
                                Active: "border", Not Active: "border-2"
                                Checked: "border-indigo-500", Not Checked: "border-transparent"
                                -->
                                <span class="pointer-events-none absolute -inset-px rounded-md" aria-hidden="true"></span>
                            </label>
                            <!-- Active: "ring-2 ring-indigo-500" -->
                            <label class="group relative flex cursor-pointer items-center justify-center rounded-md border bg-white px-4 py-3 text-sm font-medium uppercase text-gray-900 shadow-sm hover:bg-gray-50 focus:outline-none sm:flex-1">
                                <input type="radio" name="size-choice" value="XL" class="sr-only">
                                <span>XL</span>
                                <!--
                                Active: "border", Not Active: "border-2"
                                Checked: "border-indigo-500", Not Checked: "border-transparent"
                                -->
                                <span class="pointer-events-none absolute -inset-px rounded-md" aria-hidden="true"></span>
                            </label>
                            <!-- Active: "ring-2 ring-indigo-500" -->
                            <label class="group relative flex cursor-pointer items-center justify-center rounded-md border bg-white px-4 py-3 text-sm font-medium uppercase text-gray-900 shadow-sm hover:bg-gray-50 focus:outline-none sm:flex-1">
                                <input type="radio" name="size-choice" value="XXL" class="sr-only">
                                <span>XXL</span>
                                <!--
                                Active: "border", Not Active: "border-2"
                                Checked: "border-indigo-500", Not Checked: "border-transparent"
                                -->
                                <span class="pointer-events-none absolute -inset-px rounded-md" aria-hidden="true"></span>
                            </label>
                            <!-- Active: "ring-2 ring-indigo-500" -->
                            <label class="group relative flex cursor-not-allowed items-center justify-center rounded-md border bg-gray-50 px-4 py-3 text-sm font-medium uppercase text-gray-200 hover:bg-gray-50 focus:outline-none sm:flex-1">
                                <input type="radio" name="size-choice" value="XXXL" disabled class="sr-only">
                                <span>XXXL</span>
                                <span aria-hidden="true" class="pointer-events-none absolute -inset-px rounded-md border-2 border-gray-200">
                                <svg class="absolute inset-0 size-full stroke-2 text-gray-200" viewBox="0 0 100 100" preserveAspectRatio="none" stroke="currentColor">
                                    <line x1="0" y1="100" x2="100" y2="0" vector-effect="non-scaling-stroke" />
                                </svg>
                                </span>
                            </label>
                            </div>
                        </fieldset>

                        <button type="submit" class="mt-6 flex w-full items-center justify-center rounded-md border border-transparent bg-indigo-600 px-8 py-3 text-base font-medium text-white hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">Add to bag</button>
                        </form>
                    </section>
                    </div>
                </div>
                </div>
            </div>
            </div>
        </div>
    </div>
    <p v-else class="text-black dark:text-white">Здесь пока нет товаров..</p>
</template>

<script setup>
import { ref } from 'vue';

const isModalOpen = ref(false); // Состояние для управления видимостью модального окна
const selectedPost = ref(null); // Инициализация переменной для выбранного поста

const openModal = () => {
    isModalOpen.value = true; // Открыть модальное окно
};

const closeModal = () => {
    isModalOpen.value = false; // Закрыть модальное окно
};

const selectPost = (post) => {
    selectedPost.value = post; // Установить выбранный пост
    openModal(); // Открыть модальное окно после выбора поста
};

// Пример данных для постов (12 товаров)
const posts = ref([
    { id: 1, title: 'Товар 1', slug: 'product-1', category: { slug: 'category-1' }, cover: { url: '/path/to/image1.jpg', alternativeText: 'Товар 1' } },
    { id: 2, title: 'Товар 2', slug: 'product-2', category: { slug: 'category-2' }, cover: { url: '/path/to/image2.jpg', alternativeText: 'Товар 2' } },
    { id: 3, title: 'Товар 3', slug: 'product-3', category: { slug: 'category-3' }, cover: { url: '/path/to/image3.jpg', alternativeText: 'Товар 3' } },
    { id: 4, title: 'Товар 4', slug: 'product-4', category: { slug: 'category-4' }, cover: { url: '/path/to/image4.jpg', alternativeText: 'Товар 4' } },
    { id: 5, title: 'Товар 5', slug: 'product-5', category: { slug: 'category-5' }, cover: { url: '/path/to/image5.jpg', alternativeText: 'Товар 5' } },
    { id: 6, title: 'Товар 6', slug: 'product-6', category: { slug: 'category-6' }, cover: { url: '/path/to/image6.jpg', alternativeText: 'Товар 6' } },
    { id: 7, title: 'Товар 7', slug: 'product-7', category: { slug: 'category-7' }, cover: { url: '/path/to/image7.jpg', alternativeText: 'Товар 7' } },
    { id: 8, title: 'Товар 8', slug: 'product-8', category: { slug: 'category-8' }, cover: { url: '/path/to/image8.jpg', alternativeText: 'Товар 8' } },
    { id: 9, title: 'Товар 9', slug: 'product-9', category: { slug: 'category-9' }, cover: { url: '/path/to/image9.jpg', alternativeText: 'Товар 9' } },
    { id: 10, title: 'Товар 10', slug: 'product-10', category: { slug: 'category-10' }, cover: { url: '/path/to/image10.jpg', alternativeText: 'Товар 10' } },
    { id: 11, title: 'Товар 11', slug: 'product-11', category: { slug: 'category-11' }, cover: { url: '/path/to/image11.jpg', alternativeText: 'Товар 11' } },
    { id: 12, title: 'Товар 12', slug: 'product-12', category: { slug: 'category-12' }, cover: { url: '/path/to/image12.jpg', alternativeText: 'Товар 12' } },
]);

// Пример открытия модального окна при загрузке страницы
openModal();
</script>