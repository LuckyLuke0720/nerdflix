<template>
    <div class="movie-card">
      <div class="poster-container">
        <img :src="movie.urlPoster" :alt="movie.title" class="movie-poster" />
        <div class="overlay">
          <span class="rating"> {{ movie.rating }}</span>
        </div>
      </div>
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
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
 
  .movie-card {
    text-align: center;
    width: 220px;
    padding: 10px;
    background: transparent;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  }
  
  .poster-container {
    position: relative;
    overflow: hidden;
    border-radius: 6px;
  }
  
  .movie-poster {
    width: 100%;
    border-radius: 6px;
    transition: filter 0.3s ease-in-out; 
  }
  
  /* used to be able to put the rating on the top of the poster */
  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.7); 
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 1.5rem;
    font-weight: 100;
    opacity: 0;
    transition: opacity 0.3s ease-in-out; /* fade */
  }
  
  .poster-container:hover .overlay {
    opacity: 1; 
  }
  
  .poster-container:hover .movie-poster {
    filter: brightness(50%); /* darken the poster */
  }
  
  .movie-title {
    margin: 10px 0 5px;
    font-size: 1.2rem;
    font-weight: bold;
    color: white;
  }
  
  .movie-year {
    color: gray;
    font-size: 0.9rem;
  }
  </style>