<template>
    <div class="movie-card">
      <img :src="movie.urlPoster" :alt="movie.title" class="movie-poster" />
      <h3 class="movie-title">{{ movie.title }}</h3>
      <p class="movie-year">{{ movie.year }}</p>
    </div>
</template>
  
<script>
    export default {
    name: "MovieCard",
    props: {
      movie: {
        type: Object,
      }, 
    },
  };
  </script>
  
  <style scoped>
  /* Movie Card */
  .movie-card {
    text-align: center;
    width: 220px;
    padding: 10px;
    background: #fff;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  }
  
  /* Movie Poster */
  .movie-poster {
    width: 100%;
    border-radius: 6px;
  }
  
  /* Title */
  .movie-title {
    margin: 10px 0 5px;
    font-size: 1.2rem;
    font-weight: bold;
  }
  
  /* Year */
  .movie-year {
    color: gray;
    font-size: 0.9rem;
  }
  </style>