<script setup>
import { ref } from 'vue';
import BaseCard from './BaseCard.vue';

defineProps({
    task: Object,
})
const emit = defineEmits([
    "complete-task",
    "delete-task"
])

const completeTask = ref(false)
const deleteTask = () => {
    emit('delete-task')
}
</script>
<template>
    <BaseCard>

        <div class="head-card">
            <h3>{{ task.title }}</h3>
            <div class="status">
                <p v-if="completeTask">Done</p>
                <p v-else>{{ task.completed? "Done":"" }}</p>
            </div>

        </div>
        <p class="completed-status">Status: <strong>{{ task.completed ? 'Pending' : 'Completed' }}</strong> </p>
        <div class="button">
            <button class="btn-1"  @click="completeTask = true">Complete</button>
            <button class="btn-2"  @click="emit('delete-task', task.id)">Delete</button>
        </div>
    </BaseCard>
</template>
<style>
.head-card {
    height: 40px;
    display: flex;
    justify-content: space-between;
    padding-left: 40px;
    padding-right: 20px;
    
}
.status{
    height: auto;
    display: flex;
    align-items: center;
    gap: 20px;
    color: green;
    font-weight: bold;
    font-size: 20px;
    padding: 0 10px;
    margin-right: 22px;
    margin-top: 10px;
}
.completed-status{
    height: 40px;
    padding-left: 40px;
}
.completed-status strong {
    color: green;
}
.button {
    
    display: flex;
    align-items: center;
    justify-content: flex-end;
    gap: 10px;
    padding-right: 40px;
    padding-bottom: 10px;
}

.btn-1,
.btn-2 {
    padding: 10px 20px;
    border-radius: 4px;
    border: none;
}

.btn-1 {
    background: none;
    border: 2px solid green;
    color: black;
    font-weight: bold;
}

.btn-2 {
    background: none;
    border: 2px solid red;
    color: black;
    font-weight: bold;

}
</style>