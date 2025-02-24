<template>
    <div class="searchSection">
        <div class="selectedSectionName">{{ selectedSection }}</div>
        <div class="searchAndFilters">
            <SearchBar v-model="searchTerm" @typing="handleSearch"/>
            <span>
                <div class="filters">
                    <button class="filter" @click="$emit('sort-title')">Title (A-Z)
                        <BIconCaretDown />
                    </button>
                    <button class="filter" @click="$emit('sort-rating')">Rating
                        <BIconCaretDown />
                    </button>
                </div>
            </span>
        </div>
    </div>
</template>

<script>
import { BIconCaretDown } from 'bootstrap-icons-vue';
import SearchBar from './SearchBar.vue';
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'SearchSection',
    components: {
        SearchBar,
        BIconCaretDown
    },
    props: {
        selectedSection: {
            type: String,
            required: true
        }
    },
    emits: ['search-term'],
    methods: {
        handleSearch(searchTerm) {
            this.$emit('search-term', searchTerm); // Emit search term to DashboardView
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
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}

.searchSection{
    background-color: rgb(23, 23, 23);
}

.filter {
    background-color: transparent;
    border-width: 1px;
    border-color: grey;
    border-radius: 5px;
    background-color: black;
    color: white;
    cursor: pointer;
    margin-left: 10px;
}

.filters{
    display: flex;
    background-color: transparent;
    margin-right: 30px;
}
</style>