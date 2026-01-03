<script setup>
import { onMounted } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import GalleryCard from '../ui/GalleryCard.vue';


gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  
  gsap.from(".gallery-item", {
    scrollTrigger: {
      trigger: ".gallery-grid",
      start: "top 80%",
      toggleActions: "play none none reverse"
    },
    y: 60,            
    opacity: 0,       
    duration: 0.8,
    stagger: 0.1,     
    ease: "power2.out"
  });

  
  gsap.from(".gallery-title", {
    scrollTrigger: {
      trigger: ".gallery-title",
      start: "top 85%",
    },
    y: -20,
    opacity: 0,
    duration: 0.6,
    ease: "power2.out"
  });
});
</script>

<template>
    <div class="py-8 md:py-20 bg-gray-50/50"> <div class="container mx-auto px-4">
            
            <div class="gallery-title text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-primary-dark mb-2">Memorable Moments</h2>
                <div class="h-1 w-20 bg-primary mx-auto rounded-full"></div>
            </div>

            <div class="gallery-grid grid grid-cols-4 md:grid-cols-12 gap-4 md:gap-6">
                
                <div 
                    v-for="n in 6" 
                    :key="n" 
                    class="col-span-2 md:col-span-4 gallery-item"
                >
                    <GalleryCard />
                </div>

            </div>
        </div>
    </div>
</template>