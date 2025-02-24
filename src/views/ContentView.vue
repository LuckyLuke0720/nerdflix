<template>
    <div class="movies-grid">
      <!-- iterate over movies array and pass elem to MovieCard -->
      <MovieCard v-for="movie in movies" :key="movie.idIMDB" :movie="movie" />
    </div>
  </template>
  
  <script>
  import { defineComponent } from "vue";
  import MovieCard from "@/components/MovieCard.vue"; // Ensure correct path
  
  export default defineComponent({
    name: "ContentView",
    components: {
      MovieCard,
    },
    props: {
      movies: {
        type: Array,
        default: () => [],
      },
    },
  });
  </script>
  
  <style scoped>
  /* Grid Layout */
  .movies-grid {
    display: grid;
    background-color: black;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 16px;
    padding: 20px;
  }
  </style>