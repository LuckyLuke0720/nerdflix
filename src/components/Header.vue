<template>
    <div class="header">
        <div class="buttonsSection">
            <HeaderButton label="Home Page" :isSelected="selectedSection === 'Home Page'" @click="selectSection('Home Page')" />
            <HeaderButton label="Movies" :isSelected="selectedSection === 'Movies'" @click="selectSection('Movies')"/>
            <HeaderButton label="Series" :isSelected="selectedSection === 'Series'" @click="selectSection('Series')"/>
        </div>
        <div class="title">
            <h1>NerdFlix</h1>
        </div>
        <div class="fav">
            <BIconStarFill />
        </div>
    </div>
</template>

<script>
import { defineComponent, ref } from 'vue';
import { BIconStarFill } from 'bootstrap-icons-vue'
import HeaderButton from './HeaderButton.vue';

export default defineComponent({
    name: 'MainHeader',
    components: {
        HeaderButton,
        BIconStarFill
    },
    emits: ['sectionSelected'],
    setup(_, { emit }) {
        const selectedSection = ref('Home Page');

        const selectSection = (section) => {
            selectedSection.value = section;
            emit('sectionSelected', section);
        };

        return { selectedSection, selectSection };
    }
})
</script>

<style>
.header{
    background-color: black;
    width: 100%;
    flex-direction: row;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.buttonsSection{
    justify-content: flex-start;
    display: flex;
    padding-left: 30px;
}

.title{
    color: red;
    justify-content: center;
}

.fav{
    color: yellow;
    justify-content: flex-end;
    display: flex;
    padding-right: 30px;
}


</style>