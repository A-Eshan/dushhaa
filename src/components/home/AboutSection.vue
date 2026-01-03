<script setup>
    
    import { onMounted } from 'vue';
    import gsap from 'gsap';
    import { ScrollTrigger } from 'gsap/ScrollTrigger';
    import { ArrowRight } from 'lucide-vue-next'; 

    import AboutImg from '../../assets/images/home/about-img.png'  
    import ButtonText from '../ui/ButtonText.vue';

    
    gsap.registerPlugin(ScrollTrigger);

    onMounted(() => {
        const tl = gsap.timeline({
            scrollTrigger: {
                trigger: ".about-section",
                start: "top 75%",          
                toggleActions: "play none none reverse"
            }
        });

        
        tl.from(".about-img-box", {
            x: -50,            
            opacity: 0,
            duration: 1,
            ease: "power3.out"
        })
        .from(".about-content-child", {
            y: 30,             
            opacity: 0,
            duration: 0.8,
            stagger: 0.2,      
            ease: "power2.out"
        }, "-=0.6");           
    });
</script>

<template>
    <div class="about-section py-20 overflow-hidden">
        <div class="container">
            <div class="grid grid-cols-6 md:grid-cols-12 gap-6">
                
                <div class="col-span-6">
                    <div class="about-img-box">
                        <img :src="AboutImg" alt="">
                    </div>
                </div>

                <div class="col-span-6">
                    <div class="space-y-4 md:space-y-20">
                        <h1 class="about-content-child font-bold mt-0 md:mt-24">About Our Alumni Association</h1>
                        
                        <p class="about-content-child text-justify">The Dhaka University Shahidullah Hall Alumni Association is a body that connects former students of Dr. Muhammad Shahidullah Hall, one of the residential halls of the University of Dhaka. These associations play a crucial role in fostering relationships among alumni, providing networking opportunities, and supporting the university and its current students.</p>
                        
                        <div class="about-content-child flex justify-between items-end">
                            <h1 class="text-outline text-outline-thin font-poppins">EST. 1960</h1>
                            <ButtonText label="Read More" :icon="ArrowRight" iconSize="16" />
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>

<style scoped>

</style>