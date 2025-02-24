<template>
    <div class="movies-grid">
        <p v-if="movies.length === 0" class="no-movies">No movies with that title</p>
        <!-- iterate over movies array and pass elem to MovieCard -->
        <MovieCard v-for="movie in movies" :key="movie.idIMDB" :movie="movie" />
    </div>
</template>
  
<script>
import { defineComponent } from "vue";
import MovieCard from "@/components/MovieCard.vue"; 

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
 
.movies-grid {
  display: grid;
  background-color: black;
  grid-template-columns: repeat(6, 1fr);
  gap: 24px; 
  padding: 20px;
  justify-content: center;
}

.no-movies {
  grid-column: span 6; 
  text-align: center;
  color: white;
  font-size: 1.5rem;
  font-weight: bold;
  padding: 20px;
}
</style>