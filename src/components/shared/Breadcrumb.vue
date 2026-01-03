<script setup>
    defineProps({
    title: {
        type: String,
        default: 'Title'
    },
    pageName:{
        type: String,
        default: 'This is the pageName'
    }
});
</script>

<template>
    <div class="w-full h-36 md:h-64 breadcrumb-wrapper">
        <img src="../../assets/images/home/heroImg.png" class="h-full w-full object-cover position-center" alt="">
        <div class="breadcrumb-text h-full w-full bg-black/40 flex flex-col justify-center items-center text-white absolute top-0 left-0 gap-y-4 md:gap-y-6">
            <h1 class="text-2xl md:text-4xl font-bold mb-2">{{ title }}</h1>
            <p class="text-sm md:text-base">Home / {{ pageName }}</p>
        </div>
    </div>
</template>

<style>
    .breadcrumb-wrapper {
        position: relative;
    }
</style>