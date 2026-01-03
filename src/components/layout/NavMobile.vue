<script setup>
import { ref, watch, onUnmounted } from 'vue';
import gsap from 'gsap';
import { X, ArrowRight } from 'lucide-vue-next';
import ButtonBase from '../ui/ButtonBase.vue';

// 1. Props & Emits
const props = defineProps({
  isOpen: Boolean
});

const emit = defineEmits(['close']);

// 2. Data Definitions
const links = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Member', path: '/members' },
  { name: 'Contact', path: '/contact' }
];

// 3. Refs for Animation
const menuOverlay = ref(null);
const menuContent = ref(null);
const navLinksRefs = ref([]); 

// 4. Animation Function
const runAnimation = () => {
  const tl = gsap.timeline();

  tl.fromTo(menuContent.value, 
    { x: '100%' }, 
    { x: '0%', duration: 0.6, ease: 'power3.out' }
  );

  tl.fromTo(navLinksRefs.value, 
    { opacity: 0, y: 20 },
    { opacity: 1, y: 0, duration: 0.4, stagger: 0.1, ease: 'power2.out' },
    "-=0.3"
  );
};

// 5. Watcher: Handle Open/Close state
watch(() => props.isOpen, (newVal) => {
  if (newVal) {
    // Wait for render, then animate
    setTimeout(runAnimation, 10);
    // Lock scroll
    document.body.style.overflow = 'hidden';
  } else {
    // Unlock scroll
    document.body.style.overflow = 'auto';
  }
});

// 6. SAFETY FIX: Unlock scroll if component is destroyed (e.g. route change)
onUnmounted(() => {
  document.body.style.overflow = 'auto';
});

// 7. Close Function
const closeMenu = () => {
  // If menuContent is null (already closed/destroyed), just emit close
  if (!menuContent.value) {
    emit('close');
    return;
  }

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
          <router-link 
            v-for="(link, index) in links" 
            :key="link.name"
            :to="link.path"
            :ref="el => { if(el) navLinksRefs[index] = el.$el }" 
            class="text-2xl font-display font-semibold text-gray-600 transition-colors flex items-center gap-2"
            active-class="text-primary font-bold" 
            @click="closeMenu"
          >
            <span>+ {{ link.name }}</span>
            <span v-if="$route.path === link.path" class="w-2 h-2 rounded-full bg-primary mt-1"></span>
          </router-link>
        </nav>

        <div :ref="el => navLinksRefs[4] = el" class="mt-auto pt-10">
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