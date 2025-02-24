<template>
  <Header @section-selected="updateSelectedSection"/>
  <SearchSection :selectedSection="selectedSection"/>
  <ContentView :movies="movies"/>
</template>

<script>
import { ref, onMounted, watchEffect } from 'vue';
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
          console.log("movies loaded successfully:", movies.value);
        } else {
          console.error("Invalid JSON structure:", data);
        }
      } catch (error) {
        console.error("Error loading movies:", error);
      }
    });

    watchEffect(() => {
      console.log("Updated movies array:", movies.value);
    });

    return { selectedSection, updateSelectedSection, movies };
  }
}
</script>
