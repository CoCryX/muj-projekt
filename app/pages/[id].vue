<script setup lang="ts">
import Label from "~/components/Label.vue";

const route = useRoute();
const router = useRouter();

// Načteme všechna data
const profiles = useProfiles();

// Najdeme konkrétní profil podle ID z URL
const profile = computed(() => {
  const idFromUrl = Number(route.params.id);
  return profiles.value.find((p) => p.id === idFromUrl);
});

// Fallback obrázek (kopie logiky z karty)
const photoUrl = computed(() => {
  if (!profile.value) return "";
  if (profile.value.photo) return profile.value.photo;
  return profile.value.gender === "female"
    ? "https://cdn-icons-png.flaticon.com/512/6997/6997662.png"
    : "https://cdn-icons-png.flaticon.com/512/3135/3135715.png";
});

// Tlačítko zpět
const goBack = () => router.push("/");
</script>

<template>
  <div class="detail-container">
    <button @click="goBack" class="back-btn">← Zpět na seznam</button>

    <div v-if="profile" class="profile-detail">
      <img :src="photoUrl" :alt="profile.name" class="big-photo" />
      
      <h1>{{ profile.name }}</h1>
      
      <div class="meta">
        <Label theme="grey">{{ profile.age }} let</Label>
        <Label :theme="profile.gender === 'female' ? 'pink' : 'blue'">
          {{ profile.gender }}
        </Label>
      </div>

      <div class="bio-section">
        <h3>O uživateli</h3>
        <p>{{ profile.bio }}</p>
      </div>
    </div>

    <div v-else class="not-found">
      <h2>Profil nenalezen 😕</h2>
      <p>Uživatel s ID {{ route.params.id }} neexistuje.</p>
    </div>
  </div>
</template>

<style scoped>
.detail-container {
  max-width: 600px;
  margin: 40px auto;
  padding: 20px;
  font-family: sans-serif;
}

.back-btn {
  background: none;
  border: none;
  color: #3b82f6;
  font-weight: 600;
  cursor: pointer;
  margin-bottom: 20px;
  font-size: 1rem;
}

.profile-detail {
  background: white;
  padding: 40px;
  border-radius: 24px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.08);
  text-align: center;
  border: 1px solid #f3f4f6;
}

.big-photo {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 20px;
  border: 4px solid white;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}

h1 { margin-bottom: 12px; color: #111827; }

.meta {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 30px;
}

.bio-section {
  text-align: left;
  background: #f9fafb;
  padding: 20px;
  border-radius: 12px;
}

.bio-section h3 { margin-top: 0; color: #374151; font-size: 1rem; text-transform: uppercase; letter-spacing: 0.05em; }
.bio-section p { line-height: 1.6; color: #4b5563; }

.not-found { text-align: center; color: #6b7280; margin-top: 50px; }
</style>