<template>
  <Header @section-selected="updateSelectedSection"/>
  <SearchSection :selectedSection="selectedSection"/>
</template>

<script>
import { ref } from 'vue';
import Header from './components/Header.vue';
import SearchSection from './components/SearchSection.vue';
import './styles/text.css'
import './styles/containers.css'

export default {
  name: 'App',
  components: {
    Header,
    SearchSection
  },
  setup() {
    // default selected section
    const selectedSection = ref("Home Page"); 

    const updateSelectedSection = (section) => {
      selectedSection.value = section;
    };

    return { selectedSection, updateSelectedSection };
  }
}
</script>
