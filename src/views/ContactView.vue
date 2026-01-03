<script setup lang="ts">
import { PhoneCall } from 'lucide-vue-next';
import Breadcrumb from '../components/shared/Breadcrumb.vue';

</script>

<template>
    <Breadcrumb title="Contact Us" pageName="Get in Touch with Us" />
    <div class="container py-4 md:py-20">
        <div class="bg-primary p-4 w-full max-w-5xl mx-auto md:p-16 text-white text-center contact-card">
            <p class="text-3xl md:4xl mb-4 md:mb-8 font-bold">Abul Khair Mohammad Hafizullah Khan</p>
            <p class="text-xl md:text-2xl">Joint Secretary</p>
            <p class="text-xl md:text-2xl">LGD</p>
            <div class="bg-white text-primary font-bold p-2 md:p-4 mt-4 md:mt-8 inline-flex gap-x-4">
                <PhoneCall class="text-primary"/>
                <p>Cell: 01729295959</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .contact-card {
        background-image: url('../assets/images/home/contact-bg.png');
        background-size: contain;
        background-position: center;
        background-repeat: no-repeat;
    }
</style>