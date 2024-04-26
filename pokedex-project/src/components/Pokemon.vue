<script setup>
import { createApp } from 'vue';

const app = createApp({
  data() {
    return {
      pokemon: {}
    };
  },
  mounted() {
    fetch('https://pokeapi.co/api/v2/pokemon/ditto')
      .then(response => response.json())
      .then(data => this.pokemon = data);
  }
});

app.mount('#app');


</script>

<template>
<div>
    <h1>Pokemon</h1>
</div>
<main>
    <div id="app">
  <h1>{{ pokemon.name }}</h1>
  <img v-if="pokemon.sprites" :src="pokemon.sprites.front_default" alt="Pokemon Image">
  <p v-if="pokemon.types && pokemon.types.length">Types:</p>
  <ul v-if="pokemon.types && pokemon.types.length">
    <li v-for="(type, index) in pokemon.types" :key="index">{{ type.type.name }}</li>
  </ul>
  <p v-if="pokemon.height">Height: {{ pokemon.height }}</p>
  <p v-if="pokemon.weight">Weight: {{ pokemon.weight }}</p>
  <p v-if="pokemon.abilities && pokemon.abilities.length">Abilities:</p>
  <ul v-if="pokemon.abilities && pokemon.abilities.length">
    <li v-for="(ability, index) in pokemon.abilities" :key="index">{{ ability.ability.name }}</li>
  </ul>
</div>
  </main>
</template>

<style scoped>


</style>