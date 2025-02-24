<template>
    <div class="searchSection">
        <div class="selectedSectionName">{{ selectedSection }}</div>
        <div class="searchAndFilters">
            <SearchBar v-model="searchTerm" @typing="handleSearch"/>
        </div>
    </div>
</template>

<script>
import SearchBar from './SearchBar.vue';
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'SearchSection',
    components: {
        SearchBar
    },
    props: {
        selectedSection: {
            type: String,
            required: true
        }
    }
})

</script>

<style>
.selectedSectionName{
    display: flex;
    justify-content: flex-start;
    margin-left: 30px;
    color: white;
    font-size: xx-large;
    padding-top: 10px;
    padding-bottom: 10px;
    font-weight: 100;
}

.searchAndFilters{
    margin-left: 30px;
    padding-bottom: 15px;
}

.searchSection{
    background-color: rgb(23, 23, 23);
}
</style>