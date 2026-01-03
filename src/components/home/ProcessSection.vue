<script setup>
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import ButtonStroke from '../ui/ButtonStroke.vue';
import processImg from '../../assets/images/home/membership-process.png';

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
    // Master Timeline for the whole section
    const tl = gsap.timeline({
        scrollTrigger: {
            trigger: ".process-section",
            start: "top 75%",
            toggleActions: "play none none reverse"
        }
    });

    
    tl.from(".process-left-content", {
        x: -50,
        opacity: 0,
        duration: 0.8,
        ease: "power2.out"
    })
    
    
    .from(".process-line", {
        scaleY: 0,
        transformOrigin: "top", 
        duration: 0.8,
        ease: "power2.inOut"
    }, "-=0.4") 

    
    .from(".process-step", {
        x: 30,
        opacity: 0,
        duration: 0.5,
        stagger: 0.3, 
        ease: "back.out(1.7)"
    }, "-=0.4");
});
</script>

<template>
    <div class="process-section py-8 md:py-20 overflow-hidden">
        <div class="container">
            <h1 class="text-center text-primary-dark font-bold">Membership Process</h1>
        </div>
        <div class="container">
            <div class="grid grid-cols-6 md:grid-cols-12 gap-4 md:gap-8 py-4 md:py-20">
                <div class="col-span-6">
                    <div class="process-left-content">
                        <div class="w-full aspect-4/3 bg-red-500">
                            <img :src="processImg" class="w-full h-full object-cover position-center" alt="">
                        </div>
                        <ButtonStroke class="mt-8 md:mt-16 mx-auto block" label="Become a Member"/>
                    </div>
                </div>

                <div class="col-span-6">
                    <div class="process process-line border-s border-s-primary py-4 md:py-20 space-y-4 md:space-y-16 origin-top">
                        <div class="steps process-step border border-primary border-salate-300 p-4 bg-white border-s-0 w-full md:w-3/4">
                            <h6 class="text-primary font-bold mb-4">Step One</h6>
                            <p>
                                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore
                            </p>
                        </div>
                        
                        <div class="steps process-step border border-primary border-salate-300 p-4 bg-white border-s-0 w-full md:w-3/4">
                            <h6 class="text-primary font-bold mb-4">Step Two</h6>
                            <p>
                                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore
                            </p>
                        </div>
                        
                        <div class="steps process-step border border-primary border-salate-300 p-4 bg-white border-s-0 w-full md:w-3/4">
                            <h6 class="text-primary font-bold mb-4">Step Three</h6>
                            <p>
                                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore
                            </p>
                        </div>

                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<style scoped>
    .process .steps{
        position: relative;
    }
    .process .steps::before {
        content: '';
        position: absolute;
        top: 30px;
        transform: translateY(-50%);
        left: -5px;
        height: 9px;
        width: 9px;
        background-color: var(--color-primary);
    }
</style>