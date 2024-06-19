<script setup>
import { ref } from 'vue';

const eventos = ref([
  {
    id: 1,
    name: 'Concierto rata blanca',
    date: '05/07/24',
    place: 'Estadio nacional'
  },
  {
    id: 2,
    name: 'Festival de jazz',
    date: '10/01/25',
    place: 'Parque Central'
  }
]);

// Variables para el nuevo evento
const newEventName = ref('');
const newEventDate = ref('');
const newEventPlace = ref('');

// Función para agregar un nuevo evento
function addEvent() {
  if (newEventName.value && newEventDate.value && newEventPlace.value) {
    eventos.value.push({
      id: eventos.value.length + 1,
      name: newEventName.value,
      date: newEventDate.value,
      place: newEventPlace.value
    });
  }
}

// Función para eliminar un evento
function removeEvent(id) {
  eventos.value = eventos.value.filter(function(event) {
    return event.id !== id;
  });
}
</script>

<template>
  <div class="container mx-auto p-4">
    <h1 class="text-2xl font-bold mb-4">Eventos</h1>
    
    <!-- Formulario para agregar un nuevo evento -->
    <div class="mb-4">
      <input v-model="newEventName" type="text" placeholder="Nombre del evento" class="border p-2 mb-2 w-full"/>
      <input v-model="newEventDate" type="date" placeholder="Fecha del evento" class="border p-2 mb-2 w-full"/>
      <input v-model="newEventPlace" type="text" placeholder="Lugar del evento" class="border p-2 mb-2 w-full"/>
      <button @click="addEvent" class="bg-blue-500 text-white p-2 rounded">Agregar Evento</button>
    </div>
    
    <!-- Lista de eventos -->
    <div v-for="event in eventos" :key="event.id" class="border p-4 mb-4 rounded-lg shadow-lg bg-white">
      <h2 class="text-xl font-semibold">{{ event.name }}</h2>
      <p>Fecha: {{ event.date }}</p>
      <p>Lugar: {{ event.place }}</p>
      <button @click="removeEvent(event.id)" class="bg-red-500 text-white p-2 rounded">Eliminar</button>
    </div>
  </div>
</template>


