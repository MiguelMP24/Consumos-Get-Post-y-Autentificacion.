<template>
    <div style="right: 200px;">
        <ul class="grid grid-cols-2 md:grid-cols-3 gap-4 data-list">
            <li v-for="resultado in resultados" :key="resultado.id" style="width: 1844.36;">
                <a href="#" style="margin-top: 25px; margin-bottom: 25px;"
                    class="flex flex-col items-center bg-white border border-gray-200 rounded-lg shadow md:flex-row md:max-w-xl hover:bg-gray-100 dark:border-gray-700 dark:bg-gray-800 dark:hover:bg-gray-700">
                    <img v-if="personajes" :src="resultado.image" alt="imagen" class="object-cover w-full rounded-t-lg h-96 md:h-auto md:w-48 md:rounded-none md:rounded-l-lg"
                        style="height: 10vw;object-fit: cover">
                    <div class="flex flex-col justify-between p-4 leading-normal">
                        <h1 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white"> {{ resultado.name }}
                        </h1>
                    </div>
                </a>
            </li>
        </ul>
    </div>
  </template>
  <script>
  export default {
      name:'DataList',
      props:{
          resultados:Object,
          personajes:Boolean,
      }
  }
  </script>
  
  <style>
  </style>

  