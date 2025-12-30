<script setup>
import { ref } from 'vue';
import { Menu } from 'lucide-vue-next';
import NavDesktop from './NavDesktop.vue';
import NavMobile from './NavMobile.vue';

const isMenuOpen = ref(false);
</script>

<template>
  <header class="sticky top-0 z-50 w-full bg-white border-b border-gray-100 shadow-sm">
    <nav class="container flex justify-between items-center py-4">
      
      <div class="flex flex-col cursor-pointer" @click="() => {}">
        <span class="text-primary font-bold text-xl uppercase leading-tight tracking-tight">
          Shahidullah Hall
        </span>
        <span class="text-[10px] text-gray-500 uppercase tracking-[0.2em] font-semibold">
          Alumni Association
        </span>
      </div>

      <NavDesktop />

      <button 
        @click="isMenuOpen = true" 
        class="md:hidden p-2 text-gray-600 hover:text-primary transition-colors"
        aria-label="Open Menu"
      >
        <Menu :size="28" />
      </button>

      <NavMobile 
        :isOpen="isMenuOpen" 
        @close="isMenuOpen = false" 
      />
    </nav>
  </header>
</template>