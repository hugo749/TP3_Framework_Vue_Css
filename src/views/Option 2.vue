<!-------------------------------------------------------------->
<!------------------------- JS PART ---------------------------->
<!-------------------------------------------------------------->
<script setup>
import { ref, onMounted, watch } from "vue";
import axios from "axios";

const userData = ref(null);
const searchQuery = ref("");
const filteredUsers = ref([]);
const genderFilter = ref("");

const loadUsers = async () => {
    try {
        const response = await axios.get("https://randomuser.me/api/?results=54");
        userData.value = response.data.results;
        filterUsers();
    } catch (error) {
        console.error("Erreur lors de la requête à l'API randomuser.me", error);
    }
};

onMounted(loadUsers);

watch(searchQuery, () => {
    filterUsers();
});

watch(genderFilter, () => {
    filterUsers();
});

const filterUsers = () => {
    if (!userData.value) return;
    let filtered = userData.value;
    const query = searchQuery.value.toLowerCase();
    if (query) {
        filtered = filtered.filter(user => {
            const fullName = `${user.name.first} ${user.name.last}`.toLowerCase();
            return fullName.includes(query);
        });
    }
    if (genderFilter.value) {
        filtered = filtered.filter(user => user.gender === genderFilter.value);
    }
    filteredUsers.value = filtered;
};
</script>

<!-------------------------------------------------------------->
<!------------------------ HTML PART --------------------------->
<!-------------------------------------------------------------->
<template>
    <div class="columns mt-4">
        <span class="column is-justify-content-right">
        </span>
        <span class="column is-three-quarters has-text-right">
            <div class="field has-addons has-text-right is-justify-content-right">
                <p class="control">
                </p>
                <p class="control">
                    <a class="button">
                        <img src="../img/symbole-de-linterface-de-recherche.png" alt="">
                    </a>
                </p>
                <p class="control" style="width: 500px;">
                    <input class="input" type="text" v-model="searchQuery" placeholder="Vous cherchez une personne ?">
                </p>

            </div>
        </span>
    </div>
    <div>
        <!-- Recherche -->
        <div class="mt-6 pt-6">
            <!-- Affichage des utilisateurs -->
            <div class="columns is-multiline" v-if="filteredUsers">
                <div v-for="(user, index) in filteredUsers" :key="index" class="column is-one-quarter">
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
    </div>
</template>

<!-------------------------------------------------------------->
<!------------------------- CSS PART --------------------------->
<!-------------------------------------------------------------->
<style scoped>
.blockhaut {
    position: sticky;
}
</style>