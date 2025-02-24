<template>
    <div class="search-bar">
        <input type="text" v-model="searchTerm" @input="emitSearchTerm" placeholder="Search for a title"/>
        <span class="searchIcon">
            <BIconSearch />
        </span>
    </div>
</template>

<script>
import { defineComponent, ref } from 'vue';
import { BIconSearch } from 'bootstrap-icons-vue';
export default defineComponent({
    name: 'SearchBar',
    components: {
        BIconSearch,
    },
    emits: ['typing'],
    setup(_, { emit }) {
        const searchTerm = ref('');

        const emitSearchTerm = () => {
            emit('typing', searchTerm.value)//emit when text is being tyoed
        };

        return {
            searchTerm,
            emitSearchTerm,
        };
    }
});
</script>

<style scoped>
.search-bar {
    background-color: black;
    display: flex;
    align-items: center;
    padding: 5px 10px;
    border-radius: 5px;
    border-color: grey;
    width: 250px;
}

.searchIcon{
    color: grey;
}

input {
    border: none;
    outline: none;
    background: transparent;
    padding-left: 5px;
    flex-grow: 1;
}

input::placeholder {
    color: #ffffff;
}
</style>