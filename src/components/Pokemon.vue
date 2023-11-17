<template>
  <div class="c-pokemon">
    <img class="c-pokemon__image" :src="getPokemonImageUrl()" :alt="pokemonData.name" />

    <div class="c-pokemon__info">
      <header class="c-pokemon__header">
        <h2 class="c-pokemon__name">{{ pokemonData.name }}</h2>

        <label class="c-pokemon-spin" for="">
          <input class="c-pokemon-spin__input" type="checkbox" name="" id="" />

          <!-- v-if="inputTrue"  -->
          <diV class="c-pokemon-spin__symbols">
            <RefreshCcw></RefreshCcw>
            <RefreshCw></RefreshCw>
            <!-- v-if="checkbox:cheched === true" -->

            <RotateCw class="c-pokemon-spin__icon"></RotateCw>
            <RotateCcw class="c-pokemon-spin__icon"></RotateCcw>
          </diV>
        </label>
      </header>

      <p class="c-pokemon__button">More info <ChevronRight></ChevronRight></p>
    </div>
  </div>
</template>

<script setup>
//console.log(pokemonId);
import { RefreshCcw } from 'lucide-vue-next';
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

const checkClicked = function () {
  inputTrue = true;
};
</script>

<style lang="scss">
.c-pokemon {
  // display: flex;
  // flex-direction: column;

  &__image {
    margin-top: 0.5rem;
    height: 7rem;
    width: auto;
  }

  &__name {
    font-size: 1.5rem;
    font-weight: 600;

    margin-left: auto;
    margin-bottom: 0.5rem;

    &:first-letter {
      text-transform: uppercase;
    }
  }

  &__button {
    display: flex;
  }
}

.c-pokemon-spin {
  display: flex;
  flex-direction: column;

  &__symbols {
    display: flex;
    justify-content: space-between;
    margin: 1rem 0;
  }

  &__input {
    display: flex;
    flex-shrink: 0;
    align-items: center;
    justify-content: center;
    background: #111111;
    border-radius: 50%;
    height: 3rem;
    width: 3rem;
    cursor: pointer;
    margin-left: 1rem;
    transition: background 0.2s ease-in-out;
    color: white;

    &:hover {
      background: #808080;
    }

    &__input {
      display: none;
    }
  }
}
</style>
