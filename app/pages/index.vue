<script setup lang="ts">
import { ref } from 'vue';
import ProfileCard from "@/components/ProfileCard.vue"; // Pozor na jednotné číslo
import ProfileForm from "@/components/ProfileForm.vue";

// Data profilů
const profiles = ref([
  {
    name: "Anna Nováková",
    age: 17,
    gender: "female",
    photo: "https://randomuser.me/api/portraits/women/45.jpg",
    bio: "Ráda kreslí, programuje a tráví čas venku se psem. Chce se naučit Vue a dělat vlastní weby.",
  },
  {
    name: "Petr Dvořák",
    age: 18,
    gender: "male",
    // photo chybí schválně, aby se testoval fallback
    bio: "Miluje auta, zajímá se o 3D tisk a občas pomáhá ve školní dílně. Baví ho JavaScript a Arduino.",
  },
  {
    name: "Lucie Králová",
    age: 16,
    gender: "female",
    bio: "Má ráda hudbu a cestování. Učí se HTML a CSS, ale chce pochopit i základy backendu.",
  },
  {
    name: "Martin Král",
    age: 17,
    gender: "male",
    photo: "https://randomuser.me/api/portraits/men/28.jpg",
    bio: "Hraje florbal a zajímá se o kyberbezpečnost. Chtěl by dělat v IT jako etický hacker.",
  },
  {
    name: "Tereza Černá",
    age: 18,
    gender: "female",
    bio: "Zajímá ji UX design a psychologie uživatelů. Ráda navrhuje rozhraní v Figma a zkouší frontend.",
  },
]);

// Funkce pro přidání
const handleAddProfile = (payload: {
  name: string;
  age: number;
  gender: string;
  bio: string;
}) => {
  // Přidáme na začátek pole (unshift), aby byl nový profil hned vidět nahoře
  profiles.value.unshift(payload);
};
</script>

<template>
  <main class="container">
    <div class="header-section">
      <h1>Správa profilů</h1>
      <ProfileForm @add-profile="handleAddProfile" />
    </div>

    <hr class="divider" />

    <section class="profiles-grid">
      <ProfileCard
        v-for="(p, index) in profiles"
        :key="index"
        :name="p.name"
        :age="p.age"
        :gender="p.gender"
        :photo="p.photo"
        :bio="p.bio"
      />
    </section>
  </main>
</template>

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px;
  font-family: sans-serif;
}

h1 {
  margin-bottom: 20px;
}

.header-section {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-bottom: 40px;
}

.divider {
  border: 0;
  height: 1px;
  background: #e5e7eb;
  margin-bottom: 40px;
}

.profiles-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
  justify-content: flex-start; /* Zarovnání doleva jako na obrázku */
}
</style>