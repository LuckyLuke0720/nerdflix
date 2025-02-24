<template>
    <button class="headerBtn">{{ label }}</button> 
</template>

<script>
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'headerBtn',
    props: {
        label: {
            type: String,
            required: true
        }
    }
})
</script>

<style scoped>
.headerBtn{
    color: lightgray;
    background-color: transparent;
    border-top: none;
    border-left: none;
    border-right: none;
    padding-bottom: 10px;
    border-bottom-color: red;
    border-width: 5px;
    margin-right: 30px;
    font-size: medium;
}

</style>