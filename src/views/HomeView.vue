<!-------------------------------------------------------------->
<!------------------------- JS PART ---------------------------->
<!-------------------------------------------------------------->
<script setup>
import { ref, onMounted } from "vue";
import axios from "axios";

const userData = ref(null);

const loadUsers = async () => {
  try {
    const response = await axios.get("https://randomuser.me/api/?results=52");
    userData.value = response.data.results;
  } catch (error) {
    console.error("Erreur lors de la requête à l'API randomuser.me", error);
  }
};

onMounted(loadUsers);
</script>

<!-------------------------------------------------------------->
<!------------------------ HTML PART --------------------------->
<!-------------------------------------------------------------->
<template>
  <div class="columns is-multiline mt-6 pt-6" v-if="userData">
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
</template>

<!-------------------------------------------------------------->
<!------------------------- CSS PART --------------------------->
<!-------------------------------------------------------------->
<style scoped>
h1 {
  text-align: center;
  margin-top: 40px;
  font-weight: 500;
}

h2 {
  text-align: left;
  margin-top: 10px;
  font-weight: 500;
  text-decoration: underline;
}

.consignes {
  color: rgb(175, 175, 175);
  font-style: italic;
  font-size: 10px;
}
</style>
