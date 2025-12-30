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
    <button class="btn-stroke flex gap-1 items-center font-light">
        {{ label }}
        <component 
            :is="icon" 
            v-if="icon" 
            :size="iconSize" 
        />
    </button>
</template>

<style scoped>
</style>