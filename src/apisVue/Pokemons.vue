<script setup>
import { ref } from 'vue'
const pokemons = ref([])
function loadPokemons() {
    fetch('https://pokeapi.co/api/v2/pokemon')
        .then(function (response) {
            return response.json()
        })
        .then(function (data) {
            //console.log(data.results)
            for (let i = 0; i < data.results.length; i++) {
                console.log(i)
                pokemons.value.push(data.results[i])
            }
        }) 
        //se añaden elementos uno por uno a un arreglo existente 
}

</script>

<template>
    <div v-for="(pok, index) in pokemons" :key="index" class="bg-purple-300 mb-1">
        {{ pok.name }}
    </div>
    <button @click="loadPokemons">Cargar pokemons</button>


</template>