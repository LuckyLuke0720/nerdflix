<template>
    <button class="headerBtn" :class="{ active: isSelected}">{{ label }}</button> 
</template>

<script>
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'headerBtn',
    props: {
        label: {
            type: String,
            required: true
        },
        isSelected: {
            type: Boolean,
            default: false
        }
    }
})
</script>

<style scoped>
.headerBtn {
    color: lightgray;
    background-color: transparent;
    border: none;
    padding-bottom: 10px;
    margin-right: 30px;
    font-size: medium;
    cursor: pointer;
}

.headerBtn.active {
    border-bottom: 5px solid red;
}

</style>