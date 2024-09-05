<script setup>
import { ref } from 'vue'

    const evento = ref(true)

</script>
  
<template>
    <h2> Mostrar el titulo de la pelicula </h2>
    <button @click="evento = !evento">Activar evento</button>

</template>