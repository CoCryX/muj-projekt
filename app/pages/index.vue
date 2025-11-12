<script setup lang="ts">
const count = ref(0);
const names = ["Eliška", "Tomáš", "Anna", "Petr"];
</script>

<template>
  <HelloWorld/>
  <HelloUser username="Matyas"/>

  <HelloUser v-for="name in names" :key="name" :username="name" />

  <HelloUser username="John Doe" />

  <h2>Počítadlo: {{ count }}</h2>
  <button @click="count+=100">+100</button>
  <button @click="count+=10">+10</button>
  <button @click="count++">+1</button>
  <button @click="count--">-1</button>
  <button @click="count-=10">-10</button>
  <button @click="count-=100">-100</button>
</template>

<style scoped></style>

