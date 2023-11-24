<!-- Todo Layout maken -->
<!-- Todo Pijltje terug, volgende pagina en ook totaal pagina. < x / 78 > -->

<!-- Todo Prop binnen met huidige pagina -->
<!-- Todo emit met nieuwe pagina pagina -->
<!-- Todo functie om pagina te wisselen omhoog / omlaag niet onder 0 niet bovene limit -->

<template>
  <div class="c-pages">
    <button class="">
      <ChevronLeft class=""> </ChevronLeft>
    </button>

    <p class="c-page__current"></p>
    <p class="c-page__divider"></p>
    <p class="c-page__total">{{ 195 }}</p>

    <button class="c-page__action">
      <ChevronRight class="c-page__icon"> </ChevronRight>
    </button>
  </div>
</template>

<script setup>
import { ChevronRight, ChevronLeft } from 'lucide-vue-next';

</script>

<style>
.c-pages{
  text-decoration: none;
  color: white;

  display: flex;
  /* margin: 0 auto; */
  margin: 2rem;
  justify-content: center;
}
</style>
