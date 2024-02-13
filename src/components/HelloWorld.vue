<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="greetings">
    <h1 class="is-info">{{ msg }}</h1><br>
    <p class="has-text-black">En utilisant un framework CSS ainsi qu'un framework JS, réaliser un
      trombinoscope.</p><br>
    <p class="has-text-black">Les informations utilisateurs proviendront de l'API suivante :<br>
      <a class="has-text-link" href="https://randomuser.me/">Documentation de l'API ></a>
    </p><br>
    <p class="has-text-black">On affichera au moins 50 personnes en incluant : une photo, un nom, un
      prénom, un numéro de téléphone et une adresse e-mail.</p><br>
    <p class="has-text-black is-underlined">Option 1 :</p>
    <p class="has-text-black"> Ajouter des filtres pour trier par homme/femme.</p><br>
    <p class="has-text-black is-underlined">Option 2 :</p>
    <p class="has-text-black"> Ajouter une barre de recherche qui filtrera les résultats par texte.</p><br>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {

  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}</style>
