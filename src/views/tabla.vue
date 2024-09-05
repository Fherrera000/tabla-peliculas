<template>
  <div>
    <h2> Peliculas </h2>
    <table v-if="peliculas.length > 0" border="1">
      <thead>
        <tr>
          <th>Título</th>
          <th>Calificacion</th>
          <th>IMDB</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="pelicula in peliculas" :key="pelicula.id">
          <td>{{ pelicula.movie }}</td>
          <td>{{ pelicula.rating }}</td>
          <td><a :href="pelicula.imdb_url" target="_blank">{{ pelicula.imdb_url }}</a></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';

export default {
  setup() {
    const peliculas = ref([]);
    const crearTabla = async () => {
        const response = await fetch('https://dummyapi.online/api/movies');
        const data = await response.json();
        peliculas.value = data;
    };
    onMounted(() => {
      crearTabla();
    });

    return { peliculas };
  },
};
</script>
