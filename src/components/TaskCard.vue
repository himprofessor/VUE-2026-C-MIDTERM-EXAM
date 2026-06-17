<script setup>
import { defineProps, defineEmits } from 'vue';
import BaseCard from './BaseCard.vue';

const props = defineProps({
    tasks:Object
})
const emit = defineEmits(['complete', 'delete'])
</script>
<template>
    <BaseCard>
        <h2>{{ tasks.title }}</h2>
        <p>Status: {{ tasks.completed ? 'Completed' : 'Pending' }}</p> 
        <div class="button">
            <button @click="$emit('complete, task')" class="blue">Complete</button>
            <button @click="$emit('delete, task')" class="red">Delete</button>
        </div>
    </BaseCard>
</template>

<style scoped>

button{
    margin: 5px 0px 10px 20px;
    
    cursor: pointer;
    color: white;
    border-radius: 4px;
    border: none;
}

.red{
    background-color: rgb(249, 12, 12);
    
    
}
.blue{
    background-color: rgb(12, 44, 249);
}
</style>