<script setup lang="ts">
import type { Pokemon} from 'env';
 import getPokemonOptions from './api/getPokemonOptions';
 import { ref } from 'vue';
  

  
const pokemonArr = ref<Pokemon[]>([])
const pokemon = ref<Pokemon>()

const mixPokemonArray =async()=>{
  pokemonArr.value = await getPokemonOptions()
  const randomInt = Math.floor(Math.random() * 4)
  pokemon.value = pokemonArr.value[randomInt]
  console.log(pokemon.value)
}

mixPokemonArray()
</script>

<template>
<div class="flex justify-center mt-14" v-for="pokemon in pokemonArr">
    <p class="text-5xl">{{ pokemon.name }}</p>
</div>
</template>

