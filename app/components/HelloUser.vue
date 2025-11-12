<script setup lang="ts">
defineProps<{
  username: string;
}>();
</script>

<template>
  <h1>Hello, {{ username }}!</h1>
</template>

<style scoped></style>