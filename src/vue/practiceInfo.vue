<script setup>
import {ref} from 'vue';
import {defineProps} from 'vue';
let props = defineProps ({
    title: String,
    information: String
})

let iconito = ref("+");
let mostrar = ref(false); //false porque al yo darle mostrar, qué me va a aparecer? un ocultar claramente
function ocultar() {
    if (mostrar.value == false){
        mostrar.value= true;
        iconito.value="-";
    } else {
        mostrar.value=false;
        iconito.value="+";
    }

}
</script>

<template>
    <div class="bg-fuchsia-400 text-center justify-center mx-auto grid" >
        <div class="w-72 bg-fuchsia-600 text-white p-6">
            <div class="flex align-center justify-between border-b-2 border-white bg-fuchsia-900 py-3 px-2" >
                <h1>{{ title }}</h1>
                <button class="bg-fuchsia-300 text-black h-10 rounded" @click="ocultar">{{ iconito }}</button>
            </div>
            <p v-show="mostrar" class="bg-fuchsia-900">
                {{ information }}
            </p>
        </div>
    </div>

</template>