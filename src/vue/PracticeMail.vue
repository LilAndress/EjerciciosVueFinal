<script setup>
import {ref} from 'vue';
import Warning3 from '../vue3/Warning3.vue';
import Check3 from '../vue3/Check3.vue';



import {defineProps} from 'vue';
const props= defineProps({
    correo: String,
    text: String,
    date: String,
    iconIndex: Number
})

let select=ref(false); //false porque aún no ha sido leído 
let unread=ref(true);  //verdadero porque aún no ha sido leído, está unread 
function buttonSelected(){
    select.value =! select.value; 
}
function changeReadStatus (){
    select.value =! select.value; 
    unread.value= false; 
}


</script>

<template>

    <div @click="buttonSelected" class=" h-32 flex justify-around items-center bg-white border-[3px] my-3 hover:border-purple-400"   
    :class="[{'border-purple-900': select}, {'border-[3px]': select}, {'border-purple-600': !select}]">
        <div>
            <Warning3 :class="[{'text-yellow-200': !unread}, {'text-yellow-500': unread}]"  v-if="iconIndex == 0"></Warning3>
            <Check3 :class="[{'text-green-200': !unread}, {'text-green-500': unread}]"  v-if="iconIndex == 1" ></Check3>
            
        </div>
        <div class="">
            <p>{{ correo }}</p>
            <p>{{ text }}</p>
            <p>{{ date }}</p>
        </div>

    </div>

</template>