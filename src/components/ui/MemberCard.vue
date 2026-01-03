<script setup>
 import { Facebook, Twitter, Linkedin } from 'lucide-vue-next';
</script>

<template>
    <div class="border border-slate-300">
        <div class="bg-slate-100 p-4 flex justify-center items-center">
            <img src="../../assets/images/home/pro-pic.png" class="size-24 rounded-full" alt="">
        </div>
        <div class="p-2 md:p-6 space-y-2">
            <p class="text-center text-xl font-semibold">Full Name of Member</p>
            <p class="text-center text-slate-500">Designation, Company Name</p>
            <div class="flex gap-x-4 justify-center">
                <li class="flex border border-slate-300 rounded-full"><a href="" class="h-8 w-8 flex duration-300 hover:text-white hover:bg-primary rounded-full justify-center items-center"><Facebook size="16"/></a></li>
                <li class="flex border border-slate-300 rounded-full"><a href="" class="h-8 w-8 flex duration-300 hover:text-white hover:bg-primary rounded-full justify-center items-center"><Twitter size="16"/></a></li>
                <li class="flex border border-slate-300 rounded-full"><a href="" class="h-8 w-8 flex duration-300 hover:text-white hover:bg-primary rounded-full justify-center items-center"><Linkedin size="16"/></a></li>
            </div>
        </div>

    </div>
</template>

<style>

</style>