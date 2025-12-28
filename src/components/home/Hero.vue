<script setup>
import ButtonBase from '../ui/ButtonBase.vue';
import { ArrowRight, UserPlus, Download, Mail } from 'lucide-vue-next';
import { onMounted, ref } from 'vue';
import gsap from 'gsap';

// Create a reference for the element we want to animate
const heroText = ref(null);
const heroSubText = ref(null);

onMounted(() => {
  // Create a timeline for sequenced animations
  const tl = gsap.timeline();

  tl.from(heroText.value, {
    y: 50,           // Move from 50px down
    opacity: 0,      // Start invisible
    duration: 1,     // Take 1 second
    ease: "power3.out"
  })
  .from(heroSubText.value, {
    y: 30,
    opacity: 0,
    duration: 0.8,
    ease: "power3.out"
  }, "-=0.5"); // Start 0.5 seconds before the previous animation finishes
});


</script>

<template>
    <div class=" bg-red-500 h-screen relative">
        <img src="../../assets/images/home/heroImg.png" class="img-bg-cover" alt="">
        <div class="overlay flex justify-center items-center">
            <div class="text-center space-y-4">
                <h1 ref="heroText" class="text-white font-poppins">Shahidullah Hall</h1>
                <h2 ref="heroSubText" class="text-white font-poppins">Alumni Association</h2>
                <ButtonBase label="Become a Member" :icon="ArrowRight" iconSize="20" />
                <ButtonBase label="Become a Member" :icon="UserPlus" iconSize="20" />
                <ButtonBase label="Become a Member" :icon="Download" iconSize="20" />
                <ButtonBase label="Become a Member" :icon="Mail" iconSize="20" />
            </div>
        </div>
    </div>
</template>

<style scoped>
    
</style>