<template>
  <Header @section-selected="updateSelectedSection"/>
  <SearchSection :selectedSection="selectedSection" @search-term="filterMovies"/>
  <ContentView :movies="visiblemovies"/>
</template>

<script>
import { ref, onMounted } from 'vue';
import Header from './components/Header.vue';
import SearchSection from './components/SearchSection.vue';
import ContentView from './views/ContentView.vue';

import './styles/text.css'
import './styles/containers.css'

export default {
  name: 'App',
  components: {
    Header,
    SearchSection,
    ContentView,
  },

  setup() {
    // default selected section
    const selectedSection = ref("Home Page"); 
    const movies = ref([]);
    const visiblemovies = ref([]);
    console.log("Initial movies: ", movies.value);

    // keeping track of which button has been selected
    const updateSelectedSection = (section) => {
      selectedSection.value = section;
    };

    onMounted(async () => {
      try {
        const response = await fetch("/imdb-top-50.json");
        if (!response.ok) {
          throw new Error(`HTTP error! Status: ${response.status}`);
        }

        const data = await response.json();
        console.log("Fetched JSON data:", data); 

        if (data.data && Array.isArray(data.data.movies)) {
          movies.value = data.data.movies;
          visiblemovies.value = data.data.movies;
          console.log("movies loaded successfully:", movies.value);
        } else {
          console.error("Invalid JSON structure:", data);
        }
      } catch (error) {
        console.error("Error loading movies:", error);
      }
    });
    return { selectedSection, updateSelectedSection, movies };
  },
  data() {
        return {
            visiblemovies: [], //filtered list of Movies
            keyTerm: '', //inputted searchTerm from SearchBar
            // titleSortOrder: 'desc',
            // ratingSortOrder: 'asc,'
        };
    },
  
  watch: {
    //update visiblemovies when movies are fetched
    movies(newMovies) {
      this.visiblemovies = newMovies;
      console.log("visiblemovies :", this.visiblemovies);
      }
    },

  methods: {
    filterMovies(searchTerm) {
            //update searchTerm when SearchBar emits the new value
            this.keyTerm = searchTerm;
            const lowerCaseTerm = this.keyTerm.toLowerCase();

            if (!this.keyTerm) {
                this.visiblemovies = this.movies;
            } else {
                // Filter the documents based on the search term
                this.visiblemovies = this.movies.filter((mov) =>
                    mov.title.toLowerCase().includes(lowerCaseTerm));
                console.log(this.visiblemovies)
            }
        },
  },
}
</script>

<style>

#app{
  background-color: black;
  height: auto;
  width: 100%;
  min-height: 100vh;
}

</style>