<script setup>
import { ref } from 'vue'

const simpsons = ref([])

function loadPhrases() {
    fetch('https://thesimpsonsquoteapi.glitch.me/quotes?count=10')
        .then(function (response) {
            return response.json()
        })
        .then(function (data) {
            simpsons.value = data // Reemplazamos el array completo con las 10 frases
        })
    //se reemplaza todo el arreglo con un nuevo conjunto de datos 
}
</script>

<template>
    <div class="flex flex-col items-center">
        <button @click="loadPhrases" class="mb-4 px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-700">Cargar frases de los Simpsons</button>
        <div v-for="(simp, index) in simpsons" :key="index" class="card bg-purple-300 mb-4 p-4 w-1/2 rounded-lg shadow-lg">
            <div :class="{'flex-row-reverse': simp.characterDirection === 'Right', 'flex-row': simp.characterDirection === 'Left'}" class="card-content flex items-center">
                <img :src="simp.image" alt="Character Image" class="character-image w-24 h-24 m-2 rounded-full border-4 border-white shadow-lg">
                <div class="quote-content ml-4">
                    <p class="character-name text-lg font-semibold"><strong>{{ simp.character }}</strong></p>
                    <p class="quote-text text-sm text-gray-700">{{ simp.quote }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

