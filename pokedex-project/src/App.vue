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
  <header>
    <div>Pokémon</div>
  </header>

  <main>
    <div id="app">
    <h1>{{ pokemon.name }}</h1>
    <img :src="pokemon.sprites.front_default" alt="Pokemon Image">
    <p v-if="pokemon.types.length">Types:</p>
    <ul>
      <li v-for="(type, index) in pokemon.types" :key="index">{{ type.type.name }}</li>
    </ul>
    <p>Height: {{ pokemon.height }}</p>
    <p>Weight: {{ pokemon.weight }}</p>
    <p v-if="pokemon.abilities.length">Abilities:</p>
    <ul>
      <li v-for="(ability, index) in pokemon.abilities" :key="index">{{ ability.ability.name }}</li>
    </ul>
  </div>
  </main>
</template>

<style scoped>


</style>
