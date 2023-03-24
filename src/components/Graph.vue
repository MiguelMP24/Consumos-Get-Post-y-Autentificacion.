<template>
    <div>
      <h1></h1>
      <ul>
        <li v-for="character in characters" :key="character.id">
          {{ character.name }}
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        characters: [],
      };
    },
    created() {
      this.loadCharacters();
    },
    methods: {
      async loadCharacters() {
        const response = await axios.get('https://rickandmortyapi.com/api/character');
        this.characters = response.data.results;
      },
    },
  };
  </script>
  