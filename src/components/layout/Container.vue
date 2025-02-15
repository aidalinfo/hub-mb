<script setup lang="ts">
defineProps({
  class: {
    type: String,
    default: ''
  }
});
</script>

<template>
  <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8" :class="class">
    <slot />
  </div>
</template>
