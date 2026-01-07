<script setup lang="ts">
import { computed } from "vue";
// Importujeme Label, abychom ho mohli použít v template
import Label from "./Label.vue";

interface Props {
  name: string;
  age: number;
  gender: string;
  photo?: string;
  bio: string;
}

const props = defineProps<Props>();

// Fallback obrázky
const defaultPhoto = computed(() => {
  if (props.photo) return props.photo;
  return props.gender === "female"
    ? "https://cdn-icons-png.flaticon.com/512/6997/6997662.png" 
    : "https://cdn-icons-png.flaticon.com/512/3135/3135715.png";
});
</script>

<template>
  <div class="profile-card">
    <div class="image-wrapper">
      <img :src="defaultPhoto" :alt="name" class="profile-photo" />
    </div>
    
    <div class="info">
      <h2>{{ name }}</h2>
      
      <div class="tags">
        <Label theme="grey">{{ age }} let</Label>
        <Label :theme="gender === 'female' ? 'pink' : 'blue'">
          {{ gender }}
        </Label>
      </div>

      <p class="bio">{{ bio }}</p>
    </div>
  </div>
</template>

<style scoped>
.profile-card {
  background: #fff;
  border-radius: 16px; /* Kulatější rohy */
  padding: 24px;
  width: 100%;
  max-width: 400px; /* Širší karta */
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  border: 1px solid #f3f4f6;
  
  /* Flexbox pro horizontální rozložení */
  display: flex;
  align-items: flex-start;
  gap: 20px;
  text-align: left;
}

.image-wrapper {
  flex-shrink: 0;
}

.profile-photo {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  object-fit: cover;
  background-color: #f3f4f6;
}

.info {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

h2 {
  margin: 0;
  font-size: 1.25rem;
  font-weight: 700;
  color: #111827;
}

.tags {
  display: flex;
  gap: 8px;
}

.bio {
  margin: 0;
  font-size: 0.9rem;
  color: #4b5563;
  line-height: 1.4;
}
</style>