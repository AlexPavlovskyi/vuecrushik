<script setup>
import { RouterLink, RouterView } from 'vue-router'
//import Logo from './assets/logo.svg'
</script>

<template>
  <header>
    <div class="wrapper"> 
      <h1>Productivity Manager 💼</h1>
      <!-- <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="25" height="25" /> -->
      <!-- <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200" /> -->
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/exchange">Exchange Rates</RouterLink>
        <RouterLink to="/formula1">Formula 1</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
  <footer>
    <h3 class="footertitle">Productivity Manager</h3>
    <a href="https://twitter.com/AlexPavlovskyi" class="footercorp">© 2024 Copyright: Oleksii Pavlovskyi</a>
  </footer>
</template>

<style scoped>
header {
  line-height: 0.5;
  max-height: 50vh;
}
h1{
  font-size: 33px;
}
footer {
  position: fixed;
  bottom: 0;
  left: 0;
  height: 50px;
  background-color: var(--color-background-soft);
  width: 100%;
  margin-bottom: 0px;
  padding-top: 10px;
}
.footertitle{
  float: left;
  margin-left: 25px;
  padding-top: 4px;
  font-size: 17px;
  font-weight: bold;
}
.footercorp {
  float: right;
  margin-right: 25px;
  font-size: 17px;


}
h1{
  text-align: center;
  margin-bottom: 15px;
}
.logo {
  display: block;
  padding-left: 5px;
  padding-right: 5px;
  width: 50px;
  margin: auto;
  margin-bottom: 10px;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2px;
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

@media (min-width: 600px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }
.material-symbols-outlined {
  margin: 0 2rem 0 0;
  font-variation-settings:
  'FILL' 0,
  'wght' 400,
  'GRAD' 0,
  'opsz' 24
}
  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
    margin-bottom: 50px;
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
