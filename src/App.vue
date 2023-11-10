<template>
<header>
  <LogoPokemon></LogoPokemon>
</header>


  <!-- <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main> -->
</template>

<script setup>
import LogoPokemon from './components/Logo pokemon.vue';

const getPokemons = async function (limit = 15) {
  const data = await fetch(
    `https://pokeapi.co/api/v2/pokemon?limit=${limit}&offset=0`,
  ).then((r) => r.json())
}

const pokemons = ref([]);

</script>

<style scoped>
.html {
  color: #fefefe;
  background: #303030;
  font-family: 'Work Sans', sans-serif;
}
</style>
