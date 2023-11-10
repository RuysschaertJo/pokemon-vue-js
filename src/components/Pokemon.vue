<template>
  <div class="c-pokemon">
    <img class="c-pokemon__image" :src="getPokemonImageUrl()" :alt="pokemonData.name" />

    <div class="c-pokemon__info">
      <header class="c-pokemon__header">
        <h2 class="c-pokemon__name">Hey ik ben {{ pokemonData.name }}</h2>

        <label class="c-pokemon-spin" for="">
          <input class="c-pokemon-spin__input" type="checkbox" name="" id="" />
          <RotateCw class="c-pokemon-spin__icon"></RotateCw>
          <RotateCcw class="c-pokemon-spin__icon"></RotateCcw>
        </label>
      </header>

      <p class="c-pokemon__info">More info <ChevronRight></ChevronRight></p>
    </div>
  </div>
</template>

<script setup>
//console.log(pokemonId);
import { RotateCcw, RotateCw, ChevronRight } from 'lucide-vue-next';

const props = defineProps({
  pokemonData: {
    // namePo: String,
    // imgPo: String,
    type: Object,
    required: true,
  },
});

const getPokemonId = function () {
  //   url.split('/').length - 2;
  const partsOfUrl = props.pokemonData.url.split('/');
  const pokemonId = partsOfUrl[partsOfUrl.length - 2];

  //Zoals de leerkracht zegt: Zorg dat dit werkt voor de 50%.
  return pokemonId;
};

const getPokemonImageUrl = function () {
  return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/versions/generation-v/black-white/animated/${getPokemonId()}.gif `;
};
</script>

<style lang="scss">
.pokemon {
  display: flex;
  flex-direction: column;
}
</style>
