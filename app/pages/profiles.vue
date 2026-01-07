<script setup lang="ts">
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
const handleAddProfile = (payload: {
  name: string;
  age: number;
  gender: string;
  bio: string;
}) => {
  profiles.value.push(payload);
};
</script>


<template> 
  <main>
    <h1>Profily</h1>

    <ProfileForm @add-profile="handleAddProfile" />

    <section>
    <ProfilesCard
      v-for="profile in profiles"
      :key="profile.name"
      :name="profile.name"
      :age="profile.age"
      :gender="profile.gender"
      :photo="profile.photo"
      :bio="profile.bio"
    />
  </section>
  </main>
</template>

<style scoped>
section {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
  padding: 20px 0;
}
</style>
