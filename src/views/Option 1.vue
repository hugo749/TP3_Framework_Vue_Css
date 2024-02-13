<!-------------------------------------------------------------->
<!------------------------- JS PART ---------------------------->
<!-------------------------------------------------------------->
<script setup>
import { ref, onMounted, watch } from "vue";
import axios from "axios";

const userData = ref(null);
const genderFilter = ref("");

const loadUsers = async () => {
  try {
    let url = "https://randomuser.me/api/?results=50";
    if (genderFilter.value !== "") {
      url += `&gender=${genderFilter.value}`;
    }
    const response = await axios.get(url);
    userData.value = response.data.results;
  } catch (error) {
    console.error("Erreur lors de la requête à l'API randomuser.me", error);
  }
};

onMounted(loadUsers);

watch(genderFilter, loadUsers);
</script>

<!-------------------------------------------------------------->
<!------------------------ HTML PART --------------------------->
<!-------------------------------------------------------------->
<template>
  <div class="mt-6">
    <div class="control">
      <div class="select">
        <select v-model="genderFilter">
          <option value="">Tous</option>
          <option value="male">Hommes</option>
          <option value="female">Femmes</option>
        </select>
      </div>
    </div>
    <div class="columns is-multiline mt-6" v-if="userData">
      <div v-for="(user, index) in userData" :key="index" class="column is-one-quarter">
        <div class="card">
          <div class="card-image">
            <figure class="image is-4by3">
              <img :src="user.picture.large" alt="Placeholder image">
            </figure>
          </div>
          <div class="card-content">
            <div class="media">
              <div class="media-content">
                <p class="title is-4">{{ user.name.first }} {{ user.name.last }}</p>
                <p class="subtitle is-6">{{ user.email }}</p>
              </div>
            </div>
            <div class="content">
              <p><strong>Téléphone:</strong> {{ user.phone }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<!-------------------------------------------------------------->
<!------------------------- CSS PART --------------------------->
<!-------------------------------------------------------------->
<style scoped></style>
