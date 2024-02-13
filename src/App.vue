<!-------------------------------------------------------------->
<!------------------------- JS PART ---------------------------->
<!-------------------------------------------------------------->
<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<!-------------------------------------------------------------->
<!------------------------ HTML PART --------------------------->
<!-------------------------------------------------------------->
<template>
  <header>
    <nav class="navbar is-transparent">
      <a class="image is-64x64 navbar-item" href="/">
        <img src="https://assets.stickpng.com/images/580b57fcd9996e24bc43c516.png"
          alt="Bulma: a modern CSS framework based on Flexbox" class="image is-64x64">
      </a>
      <div id="navbarExampleTransparentExample" class="navbar-menu">
        <div class="navbar-start">
          <a class="navbar-item" href="/">
            Accueil
          </a>
          <a class="navbar-item" href="/option1">
            Option 1
          </a>
          <a class="navbar-item" href="/option2">
            Option 2
          </a>
          <a class="navbar-item" href="/fulloption">
            FullOption
          </a>
        </div>
      </div>
    </nav>
  </header>
  <span class="is-flex mt-6">
    <h1 class="as-text-black is-size-3 has-text-weight-bold pr-2">Bienvenu. </h1>
    <p class="has-text-grey is-size-3 has-text-weight-bold"> Sur mon app !</p>
  </span>
  <RouterView />
</template>

<!-------------------------------------------------------------->
<!------------------------- CSS PART --------------------------->
<!-------------------------------------------------------------->
<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>