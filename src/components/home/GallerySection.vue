<script setup>
import GalleryCard from '../ui/GalleryCard.vue';
</script>

<template>
    <div class= "py-8 md:py-20">
        <div class="container">
            <h1 class="text-center text-primary-dark font-bold">Gallery</h1>
        </div>
        <div class="container">
            <div class="grid grid-cols-4 md:grid-cols-12 gap-4 md:gap-6 mt-8">
                <div class="col-span-2 md:col-span-4">
                    <GalleryCard />
                </div>
                <div class="col-span-2 md:col-span-4">
                    <GalleryCard />
                </div>
                <div class="col-span-2 md:col-span-4">
                    <GalleryCard />
                </div>
                <div class="col-span-2 md:col-span-4">
                    <GalleryCard />
                </div>
                <div class="col-span-2 md:col-span-4">
                    <GalleryCard />
                </div>
                <div class="col-span-2 md:col-span-4">
                    <GalleryCard />
                </div>

            </div>
        </div>
    </div>
</template>

<style>

</style>