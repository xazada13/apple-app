<script setup>
definePageMeta({
    layout: 'products'
})
const { data: products } = await useFetch('https://fakestoreapi.com/products')
</script>

<template>
    <div class="flex flex-wrap gap-10 mx-10">

        <div v-for="p in products"
            class="flex flex-col items-center justify-center w-64 shadow-xl shadow-gray-200 p-5 hover:shadow-gray-400 rounded-lg transition-all duration-300">
            <NuxtLink :to="`/products/${p.id}`" class="flex flex-col justify-center gap-2">
                <img class="size-32" :src="`${p.image}`" alt="">
                <h1 class="text-sm">{{ p.title }}</h1>
                <p class="font">{{ p.price }}</p>
            </NuxtLink>
        </div>

    </div>
</template>
