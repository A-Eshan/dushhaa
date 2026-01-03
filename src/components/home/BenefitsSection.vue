<script setup>
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import { ArrowRight } from 'lucide-vue-next';

// 1. Register the plugin
gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
    // Check if elements exist before animating to avoid errors
    const cards = document.querySelectorAll('.benefit-card');
    
    if (cards.length > 0) {
        const tl = gsap.timeline({
            scrollTrigger: {
                trigger: ".benefits-section",
                start: "top 90%", // Trigger earlier (when top of section hits 90% of screen)
                toggleActions: "play none none reverse"
            }
        });

        tl.from(".benefit-text", {
            x: -30,
            opacity: 0,
            duration: 0.8,
            ease: "power2.out"
        })
        .from(".benefit-card", {
            x: 30,
            opacity: 0,
            duration: 0.6,
            stagger: 0.2,
            ease: "power2.out",
            clearProps: "all" // SAFETY: Removes GSAP styles after animation so they don't get stuck
        }, "-=0.6");
    }
});
</script>

<template>
    <div class="benefits-section bg-slate-100 py-8 md:py-20 overflow-hidden">
        <div class="container mx-auto px-4">
            <div class="grid grid-cols-6 md:grid-cols-12 gap-6 md:gap-12">
                
                <div class="col-span-6 md:col-span-12">
                    <h1 class="text-primary-dark text-center font-bold text-3xl mb-8">Benefits</h1>
                </div>

                <div class="col-span-6">
                    <p class="benefit-text text-justify md:py-12 text-gray-700 leading-relaxed">
                        The Dhaka University Shahidullah Hall Alumni Association, like most alumni associations, focuses on fostering connections among its former students and contributing to the betterment of the hall and the university. While specific services can vary and are often detailed on their official website (which may require direct contact or membership to access fully), here are common services and benefits offered by such associations, likely applicable to the Shahidullah Hall Alumni Association.
                    </p>
                </div>

                <div class="col-span-6">
                    <div class="space-y-4 md:space-y-8 md:py-12">
                        
                        <a class="benefit-card border border-slate-300 p-4 md:p-8 justify-between flex items-center cursor-pointer duration-300 hover:scale-105 shadow-sm">
                            <h3 class="benefits-name text-lg">Networking Opportunities</h3>
                            <div class="border border-slate-300 size-12 rounded-full flex items-center justify-center shrink-0">
                                <ArrowRight :size="24" class="text-primary" />
                            </div>
                        </a>

                        <a class="benefit-card border border-slate-300 p-4 md:p-8 justify-between flex items-center cursor-pointer duration-300 hover:scale-105 shadow-sm">
                            <h3 class="benefits-name text-lg">Career Support</h3>
                            <div class="border border-slate-300 size-12 rounded-full flex items-center justify-center shrink-0">
                                <ArrowRight :size="24" class="text-primary" />
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
}
</style>