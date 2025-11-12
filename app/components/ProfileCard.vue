<script setup lang="ts">
import { computed } from "vue";

interface Props {
  name: string;
  age: number;
  gender: "male" | "female";
  photo?: string;
  bio: string;
}

const props = defineProps<Props>();

// Výchozí obrázek podle pohlaví:
const defaultPhoto = computed(() => {
  if (props.photo) return props.photo;
  return props.gender === "female"
    ? "https://phlebotomycareertraining.com/wp-content/uploads/2023/11/default-avatar-photo-placeholder-icon-grey-vector-38519922-e1699300466746-768x768.jpg"
    : "https://connectkaro.org/wp-content/uploads/2019/03/placeholder-profile-male-500x500.png";
});
</script>

<template>
  <div class="profile-card">
    <img :src="defaultPhoto" :alt="name" class="profile-photo" />
    <h2>{{ name }}</h2>
    <p><strong>Věk:</strong> {{ age }}</p>
    <p><strong>Pohlaví:</strong> {{ gender }}</p>
    <p class="bio">{{ bio }}</p>
  </div>
</template>

<style scoped>
.profile-card {
  background: #fff;
  border-radius: 10px;
  padding: 1rem;
  width: 250px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  text-align: center;
}
.profile-photo {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 0.5rem;
}

</style>
