<script setup lang="ts">
defineProps<{
  theme: "pink" | "blue" | "grey";
}>();
</script>

<template>
  <span :class="['label', theme]">
    <slot />
  </span>
</template>

<style scoped>
.label {
  display: inline-flex;
  align-items: center;
  padding: 4px 10px;
  font-size: 0.75rem; /* Menší písmo */
  border-radius: 9999px;
  font-weight: 600;
  border: 1px solid transparent;
}

.grey {
  background: #f3f4f6;
  color: #4b5563;
  border-color: #e5e7eb;
}

.pink {
  background: #fce7f3;
  color: #be185d;
  border-color: #fbcfe8;
}

.blue {
  background: #dbeafe;
  color: #1e40af;
  border-color: #bfdbfe;
}
</style>