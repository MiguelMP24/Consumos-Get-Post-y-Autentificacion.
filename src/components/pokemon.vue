<script >
import axios from 'axios';
export default {
    data() {
        return {
            searchInput: '',
            pokemon: null
        };
    },
    methods: {
        searchPokemon() {
            axios.get(`https://pokeapi.co/api/v2/pokemon/${this.searchInput.toLowerCase()}`)
                .then(response => {
                    this.pokemon = response.data;
                })
                .catch(error => {
                    console.log(error);
                });
        }
    }
};
</script>

<template>

        <input v-model="searchInput" type="text" placeholder="Ingrese el nombre o ID del poekmon">
        <button @click="searchPokemon()">Buscar</button>
        <div v-if="pokemon" class="relative overflow-x-auto"   style="position: absolute;left: -150px; width: 1500px;">
            <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
                <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                    <tr>
                        <th scope="col" class="px-6 py-3">
                            ID
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Nombre
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Altura
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Peso
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Tipo
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Habilidad/es
                        </th>
                        <th scope="col" class="px-6 py-3">
                            Especie
                        </th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700">
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                            {{ pokemon.id }}
                        </th>
                        <td class="px-6 py-4">
                            {{ pokemon.name }}
                        </td>
                        <td class="px-6 py-4">
                            {{ pokemon.height }} M
                        </td>
                        <td class="px-6 py-4">
                            {{ pokemon.weight }} Kg
                        </td>
                        <td class="px-6 py-4">
                            {{ pokemon.types.map(typesItem => typesItem.type.name).join(', ') }}
                        </td>
                        <td class="px-6 py-4">
                            {{ pokemon.abilities.map(abilityItem => abilityItem.ability.name).join(', ') }}
                        </td>
                        <td class="px-6 py-4">
                            {{ pokemon.species.name }}
                        </td>
                    </tr>
                </tbody>
            </table>
            <img :src="pokemon.sprites.front_default" :alt="pokemon.name">
            <img :src="pokemon.sprites.front_shiny" :alt="pokemon.name">
        </div>
</template>

<style scoped>
table {
    border-collapse: collapse;
    width: 100%;
}

th,
td {
    border: 1px solid black;
    padding: 8px;
}

th {
    background-color: white;
    text-align: center;
}

input {
    left: 425px;
    color: black;
}

button {
    left: 500px;
}

img {
    position: relative;
    top: 150px;
    left: 300px;
    height: 300px;
}</style>