<script setup>

defineProps({
  label: {
    type: String,
    default: 'Click Me'
  },
  // We pass the actual Icon component as a prop
  icon: {
    type: [Object, Function], 
    default: null
  },
  iconSize: {
    type: [Number, String],
    default: 20
  }
});
</script>

<template>
    <a class="text-primary underline underline-offset-4 cursor-pointer flex gap-1 items-center font-light">
        {{ label }}
        <component 
            :is="icon" 
            v-if="icon" 
            :size="iconSize" 
        />
    </a>
</template>

<style scoped>
</style>