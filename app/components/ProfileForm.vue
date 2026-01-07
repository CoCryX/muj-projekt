<script setup lang="ts">
import { ref } from 'vue';

const newProfile = ref({
  name: "",
  age: null as number | null, // Změna na null pro placeholder
  gender: "male", // Defaultní hodnota
  bio: "",
});

type Profile = {
  name: string;
  age: number;
  gender: string;
  bio: string;
};

const emit = defineEmits<{
  (e: "add-profile", payload: Profile): void;
}>();

const handleSubmit = () => {
  // Validace - nepustí prázdné
  if (!newProfile.value.name || !newProfile.value.age) return;

  emit("add-profile", {
    name: newProfile.value.name,
    age: newProfile.value.age,
    gender: newProfile.value.gender,
    bio: newProfile.value.bio,
  });

  // Reset formuláře
  newProfile.value = {
    name: "",
    age: null,
    gender: "male",
    bio: "",
  };
};
</script>

<template>
  <form class="profile-form" @submit.prevent="handleSubmit">
    <input v-model="newProfile.name" type="text" placeholder="Jméno" required />

    <input v-model="newProfile.age" type="number" placeholder="Věk" required />

    <select v-model="newProfile.gender">
      <option value="male">male</option>
      <option value="female">female</option>
    </select>

    <textarea v-model="newProfile.bio" placeholder="Krátký popis"></textarea>

    <button type="submit">Přidat profil</button>
  </form>
</template>

<style scoped>
.profile-form {
  width: 100%;
  max-width: 400px; /* Aby odpovídal šířce karet */
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 24px;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  background: #ffffff;
  /* Odstranění stínu pro čistší vzhled, nebo nechat jemný */
}

input,
select,
textarea {
  padding: 12px;
  border-radius: 6px;
  border: 1px solid #d1d5db;
  background: #ffffff;
  font-size: 0.95rem;
  width: 100%;
  box-sizing: border-box;
}

textarea {
  min-height: 80px;
  resize: vertical;
}

button {
  padding: 12px;
  border-radius: 6px;
  background: #3b82f6;
  color: white;
  border: none;
  cursor: pointer;
  font-weight: 600;
  transition: background 0.2s;
}

button:hover {
  background: #2563eb;
}
</style>