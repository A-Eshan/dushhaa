<script setup>
import { ArrowRight } from 'lucide-vue-next';
import ButtonStroke from '../ui/ButtonStroke.vue';

// Define the links here so they are easy to update later
const navLinks = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Member', path: '/members' },
  { name: 'Contact', path: '/contact' }
];
</script>

<template>
  <div class="hidden md:flex items-center gap-10">
    
    <ul class="flex items-center gap-8">
      <li v-for="link in navLinks" :key="link.name">
        
        <router-link 
          :to="link.path" 
          class="relative text-sm font-medium text-gray-600 hover:text-primary transition-colors duration-300 group"
          active-class="text-primary font-bold" 
        >
          {{ link.name }}
          
          <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-primary transition-all duration-300 group-hover:w-full"></span>
          
          <span v-if="$route.path === link.path" class="absolute -bottom-1 left-0 w-full h-0.5 bg-primary"></span>
        </router-link>

      </li>
    </ul>

    <div class="h-6 w-px bg-gray-200"></div>

    <ButtonStroke 
      label="Become a member" 
      :icon="ArrowRight" 
      class="text-sm px-5 py-2"
    />
  </div>
</template>