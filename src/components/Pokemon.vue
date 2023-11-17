<template>
  <div class="c-pokemon">
    <img class="c-pokemon__image" :src="getPokemonImageUrl()" :alt="pokemonData.name" />

    <div class="c-pokemon__info">
      <header class="c-pokemon__header">
        <h2 class="c-pokemon__name">{{ pokemonData.name }}</h2>

        <label class="c-pokemon-spin" :for="pokemonData.name">
          <input class="c-pokemon-spin__input sr-only" type="checkbox" v-model="showBack" :id="pokemonData.name" />

          <span class="sr-only">Toggle Pokemon from back to front and vice versa.</span>

          <RefreshCw v-if="showBack" class="c-pokemon-spin__icon"></RefreshCw>
          <RefreshCcw v-else class="c-pokemon-spin__icon"></RefreshCcw>
        </label>
      </header>

      <p class="c-pokemon__button">More info <ChevronRight></ChevronRight></p>
    </div>
  </div>
</template>

<script setup>
//console.log(pokemonId);
import { RefreshCcw, RefreshCw } from 'lucide-vue-next';
import { ChevronRight } from 'lucide-vue-next';
import { ref } from 'vue';

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
  const baseUrl = `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/versions/generation-v/black-white/animated`;

  if (showBack.value) {
    return `${baseUrl}/back/${getPokemonId()}.gif`;
  }
  return `${baseUrl}/${getPokemonId()}.gif`;
};

//Todo variable of je de voor of achterkant toont.
//Todo Koppel deze variable aan de checkbox
//Todo toon aan de hand can de variable de juiste iconen.
//Todo toon aan de hand can de variable de juiste image.
//Todo voorzie een goede focus
//Todo verberg de orginele checkbox.
const showBack = ref(false);

const checkFfront = function () {
  inputTrue = true;
};
</script>

<style lang="scss">
.c-pokemon {
  //Mobile first methode.
  width: 100%;
  &__image {
    margin-top: 0.5rem;
    height: 7rem;
    width: auto;
    display: block;
    margin-bottom: -0.5rem;
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
    align-items: center;
    gap: 0.5rem;

    padding: 1rem 0;
    font-size: 0.75rem;
    margin: 0 0 0 auto;
    text-decoration: underline;
  }

  &__info {
    display: flex;
    flex-direction: column;
    background-color: #444;
    color: #fff;
    padding: 0.5rem;
    border-radius: 1rem 2rem 1rem 2rem;
    width: auto;
  }

  &__header {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &-spin {
    display: flex;
    flex-shrink: 0;

    align-items: center;
    justify-content: center;

    background: #111;
    border-radius: 50%;

    height: 3rem;
    width: 3rem;

    cursor: pointer;
    margin-left: 1rem;
    transition: background 0.2s ease-in-out;

    &:hover {
      background: #808080;
    }

    &:focus-within {
      outline: 3px solid lightcyan;
    }

    &__symbols {
      display: flex;
      justify-content: space-between;
      margin: 1rem 0;
    }

    &__input {
      position: absolute;
      width: 1px;
      height: 1px;
      padding: 0;
      margin: -1px;
      overflow: hidden;
      clip: rect(0, 0, 0, 0);
      white-space: nowrap;
      border-width: 0;
    }

    // &__input {
    //   display: flex;
    //   flex-shrink: 0;
    //   align-items: center;
    //   justify-content: center;
    //   background: #111111;
    //   border-radius: 50%;
    //   height: 3rem;
    //   width: 3rem;
    //   cursor: pointer;
    //   margin-left: 1rem;
    //   transition: background 0.2s ease-in-out;
    //   color: white;

    //   &:hover {
    //     background: #808080;
    //   }

    //   &__input {
    //     display: none;
    //   }
    // }
  }
}

//Maak de pokemons:

//vanaf 480px
@media (min-width: 480px) {
  .c-pokemon {
    width: calc((100% - 1 * 2rem) / 2);
  }
}

//vanaf 768px
@media (min-width: 768px) {
  .c-pokemon {
    width: calc((100% - 3 * 2rem) / 4);
  }
}

.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
</style>
