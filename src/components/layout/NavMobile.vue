<script setup>
import { ref, onMounted, watch } from 'vue';
import gsap from 'gsap';
import { X, ArrowRight } from 'lucide-vue-next';
import ButtonBase from '../ui/ButtonBase.vue';

const props = defineProps({
  isOpen: Boolean
});

const emit = defineEmits(['close']);

// Refs for GSAP targets
const menuOverlay = ref(null);
const menuContent = ref(null);
const navLinks = ref([]);

// Animation Logic
const runAnimation = () => {
  const tl = gsap.timeline();

  // 1. Slide in the main drawer
  tl.fromTo(menuContent.value, 
    { x: '100%' }, 
    { x: '0%', duration: 0.6, ease: 'power3.out' }
  );

  // 2. Staggered fade-in for links
  tl.fromTo(navLinks.value, 
    { opacity: 0, y: 20 },
    { opacity: 1, y: 0, duration: 0.4, stagger: 0.1, ease: 'power2.out' },
    "-=0.3" // Start slightly before drawer finishes
  );
};

// Watch for the isOpen prop to trigger animations
watch(() => props.isOpen, (newVal) => {
  if (newVal) {
    // Small timeout to ensure DOM is rendered before animating
    setTimeout(runAnimation, 10);
    // Prevent scrolling when menu is open
    document.body.style.overflow = 'hidden';
  } else {
    document.body.style.overflow = 'auto';
  }
});

const closeMenu = () => {
  gsap.to(menuContent.value, {
    x: '100%',
    duration: 0.5,
    ease: 'power3.in',
    onComplete: () => emit('close')
  });
};
</script>

<template>
  <Teleport to="body">
    <div v-if="isOpen" ref="menuOverlay" class="fixed inset-0 z-[100] flex justify-end">
      
      <div class="absolute inset-0 bg-black/40 backdrop-blur-sm" @click="closeMenu"></div>

      <div ref="menuContent" class="relative w-[85%] max-w-sm h-full bg-white shadow-2xl p-8 flex flex-col">
        
        <div class="flex justify-between items-center mb-12">
          <div class="flex flex-col">
            <span class="text-primary font-bold text-lg uppercase leading-tight">Shahidullah Hall</span>
            <span class="text-xs text-gray-400 uppercase tracking-tighter">Alumni Association</span>
          </div>
          <button @click="closeMenu" class="p-2 hover:bg-gray-100 rounded-full transition-colors">
            <X :size="28" class="text-gray-600" />
          </button>
        </div>

        <nav class="flex flex-col gap-6">
          <a v-for="(link, index) in ['Home', 'About', 'Member', 'Contact']" 
             :key="link"
             :ref="el => navLinks[index] = el"
             href="#" 
             class="text-2xl font-display font-semibold text-primary-dark hover:text-primary transition-colors"
             @click="closeMenu"
          >
            + {{ link }}
          </a>
        </nav>

        <div :ref="el => navLinks[4] = el" class="mt-auto pt-10">
          <ButtonBase 
            label="Become a member" 
            :icon="ArrowRight" 
            class="w-full py-4 text-lg" 
          />
        </div>

      </div>
    </div>
  </Teleport>
</template>