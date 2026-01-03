<script setup>
import { onMounted, ref } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

// 1. Create an array to store the DOM elements
const counters = ref([]);

// 2. Define the data for each counter (Value + Suffix)
// This matches your HTML: 60, 5K+, 17, 10+
const statsData = [
  { value: 60, suffix: '' },
  { value: 5, suffix: 'K+' },
  { value: 17, suffix: '' },
  { value: 10, suffix: '+' }
];

onMounted(() => {
  // 3. Loop through each counter element
  counters.value.forEach((el, index) => {
    const data = statsData[index];
    const proxy = { val: 0 }; // A helper object to animate numbers 0 -> Target

    gsap.to(proxy, {
      val: data.value,
      duration: 2,
      ease: "power2.out",
      scrollTrigger: {
        trigger: ".stat-section", // Start when the main section is visible
        start: "top 85%",
        toggleActions: "play none none reverse"
      },
      // 4. Update the text on every frame of the animation
      onUpdate: () => {
        // Math.ceil removes decimals (e.g., 1.5 -> 2)
        if (el) el.innerText = Math.ceil(proxy.val) + data.suffix;
      }
    });
  });
});
</script>

<template>
    <div class="stat-section about-section py-20">
        <div class="container">
            <div class="grid grid-cols-3 md:grid-cols-12 gap-6">
                
                <div class="col-span-3">
                    <div class="md:border-e border-e-gray-300 md:ps-8">
                        <div :ref="el => counters[0] = el" class="text-3xl md:text-6xl font-body font-bold text-primary">0</div>
                        <div class="text-gray-500">Years of Glory</div>
                    </div> 
                </div>

                <div class="col-span-3">
                    <div class="md:border-e border-e-gray-300 md:ps-8">
                        <div :ref="el => counters[1] = el" class="text-3xl md:text-6xl font-body font-bold text-primary">0</div>
                        <div class="text-gray-500">Proud Members</div>
                    </div> 
                </div>

                <div class="col-span-3">
                    <div class="md:border-e border-e-gray-300 md:ps-8">
                        <div :ref="el => counters[2] = el" class="text-3xl md:text-6xl font-body font-bold text-primary">0</div>
                        <div class="text-gray-500">Events Completed</div>
                    </div> 
                </div>

                <div class="col-span-3">
                    <div class="md:ps-8">
                        <div :ref="el => counters[3] = el" class="text-3xl md:text-6xl font-body font-bold text-primary">0</div>
                        <div class="text-gray-500">Overseas Alumnies</div>
                    </div> 
                </div>

            </div>
        </div>
    </div>
</template>

<style scoped>
/* No CSS changes needed */
</style>