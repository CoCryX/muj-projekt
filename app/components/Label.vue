<script setup lang="ts">
defineProps<{
  theme: "pink" | "blue" | "grey";
}>();
</script>

<template>
  <span :class="theme">
    <slot />
  </span>
</template>

<style scoped>
span {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 6px 10px;
  font-size: 0.875rem;
  border-radius: 9999px;
  border: 1px solid #e5e7eb;
  background: #f3f4f6;
  color: #374151;
}

.grey {
  background: #f3f4f6;
}

.pink {
  background: #fde8f3;
  border-color: #f9a8d4;
  color: #be185d;
}

.blue {
  background: #e6f0ff;
  border-color: #93c5fd;
  color: #1e3a8a;
}
</style>