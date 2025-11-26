<script setup lang="ts">


const profiles = [
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
];
</script>

<template>
  <div class="profiles">
    <h1>Uživatelské profily</h1>

    <div class="profiles-grid">
      <ProfileCard
        v-for="(p, index) in profiles"
        :key="index"
        :name="p.name"
        :age="p.age"
        :gender="p.gender"
        :photo="p.photo"
        :bio="p.bio"
      />
    </div>
  </div>
</template>

<style scoped>
.profiles {
  padding: 2rem;
  text-align: center;
}
.profiles-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
  justify-content: center;
  margin-top: 2rem;
}
</style>
