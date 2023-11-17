<template>
  <header>
    <LogoPokemon></LogoPokemon>
    <div class="c-pok">
      <LoadingSkeletons v-if="loading" :amount="20"></LoadingSkeletons>
      <SinglePokemon v-else v-for="pokemon in pokemons.results" :key="pokemon.name" :pokemonData="pokemon">
        <!-- key betekent dat het kan weten wat wat is.  -->
      </SinglePokemon>
    </div>
  </header>

  <!-- <p v-for="pokemon in pokemons.results">
    {{ pokemon.name }}
  </p> -->
</template>

<script setup>
import LoadingSkeletons from './components/LoadingSkeletons.vue';
import LogoPokemon from './components/Logopokemon.vue';
import SinglePokemon from './components/Pokemon.vue';
import { ref } from 'vue';

const pokemons = ref();
const loading = ref(true);

const getPokemons = async function (limit = 20) {
  const data = await fetch(`https://pokeapi.co/api/v2/pokemon?limit=${limit}&offset=0`).then((r) => r.json());
  // console.log(data);

  pokemons.value = data;
  loading.value = false;
  console.log(pokemons.value);
};

getPokemons();
</script>

<style lang="scss">
html {
  color: #fefefe;
  background: #303030;
  font-family: 'Work Sans', sans-serif;
}

.c-pok {
  display: flex;
  flex-wrap: wrap;
  //align-items: baseline;
  //Orgineel voor verschillende hoogtes;
  justify-content: space-between;
  margin: 0 auto;
  width: 100vh;
  //max-width: 72rem;
  //padding: 2rem;

  gap: 2rem;
}
</style>
