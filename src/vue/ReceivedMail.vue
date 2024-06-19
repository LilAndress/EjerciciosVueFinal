<script setup>
    import { ref } from 'vue'
    import Warning from '../vue2/Warning.vue';
    import Cancel from '../vue2/Cancel.vue';
    import Check from '../vue2/Check.vue';
    import Info from '../vue2/Info.vue';

    const props = defineProps({
        name: String,
        text: String,
        date: String,
        iconIndex: Number
    })
    let selected = ref(false) 
    let unread = ref(true)
    function buttonSelected() {
        selected.value = ! selected.value
    }
    function changeReadStatus() {
        selected.value = ! selected.value
        unread.value = false
    }
</script>

<template>
    <section @click="buttonSelected" class="group h-24 flex flex-row justify-around items-center bg-white border-[3px] my-1 hover:border-blue-300"
    :class="[{'border-blue-500': selected}, {'border-[3px]': selected}, {'border-white': !selected}]">
        <div>
            <Warning :class="[{'text-yellow-200': !unread}, {'text-yellow-500': unread}]"  v-if="iconIndex == 0"></Warning>
            <Check :class="[{'text-green-200': !unread}, {'text-green-500': unread}]"  v-if="iconIndex == 1"></Check>
            <Info :class="[{'text-blue-300': !unread}, {'text-blue-500': unread}]"  v-if="iconIndex == 2"></Info>
            <Cancel :class="[{'text-red-300': !unread}, {'text-red-500': unread}]"  v-if="iconIndex == 3"></Cancel>
        </div>
        <div>
            <div></div>
            <div class="flex flex-col items-start justify-center">
                <p class="text-lg" :class="[{'font-bold': unread}]">{{ name }}</p>
                <p class="text-sm">{{ text }}</p>
                <p class="text-xs text-gray-400">{{ date }}</p>
            </div>
        </div>
        <div class="w-[100px] flex h-full justify-start items-start mt-3">
            <button v-if="unread" @click="changeReadStatus" class="group-hover:block hidden text-xs text-gray-400">Marcar como leido</button>
        </div>
    </section>
</template>