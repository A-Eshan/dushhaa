<script setup>
import { ArrowRight } from 'lucide-vue-next';
import ButtonStroke from '../ui/ButtonStroke.vue';

// Define the links here so they are easy to update later
const navLinks = [
  { name: 'Home', href: '#' },
  { name: 'About', href: '#' },
  { name: 'Member', href: '#' },
  { name: 'Contact', href: '#' }
];
</script>

<template>
  <div class="hidden md:flex items-center gap-10">
    
    <ul class="flex items-center gap-8">
      <li v-for="link in navLinks" :key="link.name">
        <a 
          :href="link.href" 
          class="relative text-sm font-medium text-gray-600 hover:text-primary transition-colors duration-300 group"
        >
        {{ link.name }}
          
          <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-primary transition-all duration-300 group-hover:w-full"></span>
        </a>
      </li>
    </ul>

    <div class="h-6 w-[1px] bg-gray-200"></div>

    <ButtonStroke 
      label="Become a member" 
      :icon="ArrowRight" 
      class="text-sm px-5 py-2"
    />
  </div>
</template>