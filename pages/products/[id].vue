<template>
 <div class="flex flex-wrap w-auto mx-[100px] my-[50px] gap-[200px] justify-center">
    <img class="xl:w-[600px] lg:w-[400px]" :src="`${product.image}`" alt="">
    <div class="flex flex-col gap-10 lg:w-1/3 justify-center">
        <h1 class="text-4xl font-bold">{{ product.title }}</h1>
        <p class="text-xl font-semibold">{{ product.description }}</p>
        <p class="text-lg font-medium">${{ product.price }}</p>
    </div>
 </div>
</template>
<script setup>
const {id} = useRoute().params
const uri = 'https://fakestoreapi.com/products/' + id
const {data: product} = await useFetch(uri)
if (!product.value){
    throw createError({statusCode: 404, statusMessage: 'Product not found'})
}
</script>