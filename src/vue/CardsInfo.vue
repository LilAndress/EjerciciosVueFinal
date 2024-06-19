<script setup>
    import { ref } from 'vue';
    import { defineProps } from 'vue';
    let props = defineProps({
        title: String,
        information: String
    })
    let palabra = ref("Mostrar");
    let mostrar = ref(false);
    function ocultar(){
        if(mostrar.value == false){
            mostrar.value = true;
            palabra.value = "Ocultar";
        }
        else{
            mostrar.value = false;
            palabra.value = "Mostrar";
        }
        
    }
</script>
<template>
    <div class="bg-zinc-300 grid mx-auto text-center justify-center">
        <div class="w-60 bg-black text-white p-6">
            <div class="flex justify-between border-b-2 border-white bg-slate-800 py-3 px-2 align-center">
                <h1>{{ title }}</h1>
            <button class="bg-white h-10 rounded text-black"
                @click="ocultar">
                {{ palabra }}
            </button>
            </div>
            <p v-show="mostrar" class="bg-slate-800">
               {{ information }}
            </p>

        </div>
   
    </div>
</template>