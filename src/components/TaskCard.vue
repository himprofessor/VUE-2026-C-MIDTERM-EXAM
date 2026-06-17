<script setup>

import BaseCard from './BaseCard.vue';

const props = defineProps({
    task : Object
})
const emit = defineEmits([
    'button-click',
    
])


function handleClick(){
    emit('button-click', props.task.id)
}

function handlesComplete(){
    emit ('complete-task', props.task)
}
function deleteTask(){
    emit ('delete-task', props.task.id)
}


</script>

<template>
    <BaseCard>
        <h1>{{ task.title }}</h1>
        <p>{{ task.completed }}</p>
        <button @click="handleClick">Emits</button>
        <button @click="handlesComplete">Complete</button>
        <button @click="deleteTask">Delete</button>
        
    </BaseCard>
</template>

<style scoped>


</style>