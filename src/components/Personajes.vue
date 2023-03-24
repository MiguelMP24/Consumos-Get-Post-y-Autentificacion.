<script>

import { public_key, secret_key } from './Marvel.vue';
import axios from 'axios';

export default {
    name: 'characters',

    data() {
        return {
            characters: []
        }
    },

    mounted() {
        this.getPersonajes()
    },
    methods: {
        getPersonajes: function () {
            axios.get(`http://gateway.marvel.com/v1/public/characters?apikey=${public_key}`)//Aqui mandamos llamar la api asi como anuestra api key con la que va a funcionar
                .then((result) => {

                    result.data.data.results.forEach((item) => {
                        console.log(item)//traemos los resultados donde estos seran mostrados en la consola para despues poder despues mostrarlos dentro de la pagina

                        this.characters.push(item)
                    })
                })
                .catch((error) => {
                    console.log(error);
                })
        }
    }
}

</script>

<template>
    <div style="right: 200px;">
        <ul class="grid grid-cols-2 md:grid-cols-3 gap-4">
            <li v-for="character in characters" style="width: 1844.36;">
                <a href="#" style="margin-top: 25px; margin-bottom: 25px;"
                    class="flex flex-col items-center bg-white border border-gray-200 rounded-lg shadow md:flex-row md:max-w-xl hover:bg-gray-100 dark:border-gray-700 dark:bg-gray-800 dark:hover:bg-gray-700">
                    <img class="object-cover w-full rounded-t-lg h-96 md:h-auto md:w-48 md:rounded-none md:rounded-l-lg"
                        :src="character.thumbnail.path + '.' + character.thumbnail.extension" alt=""
                        style="height: 10vw;object-fit: cover">
                    <div class="flex flex-col justify-between p-4 leading-normal">
                        <h1 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ character.name
                        }}<!--Aqui mandamos llamar a los parametros que la api nos ofrece-->
                        </h1>
                        <p class="mb-3 font-normal text-gray-700 dark:text-gray-400"> {{ character.description }}</p>
                    </div>
                </a>
            </li>
        </ul>
    </div>
</template> 

<style></style>