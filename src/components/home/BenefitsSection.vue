<script setup>
    import { ArrowRight } from 'lucide-vue-next';
</script>

<template>
    <div class="benefits-section bg-slate-100 py-8 md:py-20">
        <div class="container">
            <div class="grid grid-cols-6 md:grid-cols-12 gap-6 md:gap-12">
                <div class="col-span-6 md:col-span-12">
                    <h1 class="text-primary-dark text-center font-bold">Benefits</h1>
                </div>
                <div class="col-span-6">
                    <p class="text-justify md:py-12">
                        The Dhaka University Shahidullah Hall Alumni Association, like most alumni associations, focuses on fostering connections among its former students and contributing to the betterment of the hall and the university. While specific services can vary and are often detailed on their official website (which may require direct contact or membership to access fully), here are common services and benefits offered by such associations, likely applicable to the Shahidullah Hall Alumni Association
                    </p>
                </div>
                <div class="col-span-6">
                    <div class="space-y-4 md:space-y-8 md:py-12">
                        <a class="border border-slate-300 p-4 md:p-8 justify-between flex cursor-pointer duration-300 hover:scale-105">
                            <h3 class="benefits-name">Networking opportunities</h3>
                            <div class="border border-slate-300 size-12 rounded-full flex items-center justify-center">
                                <ArrowRight size="24" class="text-primary" />
                            </div>
                        </a>
                        <a class="border border-slate-300 p-4 md:p-8 justify-between flex cursor-pointer duration-300 hover:scale-105">
                            <h3 class="benefits-name">Career Support</h3>
                            <div class="border border-slate-300 size-12 rounded-full flex items-center justify-center">
                                <ArrowRight size="24" class="text-primary" />
                            </div>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.benefits-name {
    font-weight: 600;
    line-height: 2;
}
</style>