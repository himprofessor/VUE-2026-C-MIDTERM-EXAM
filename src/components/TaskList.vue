<template>
    <div class="select">
        <button class="btn-select" id="all" @click="all">All</button>
        <button class="btn-select" id="complete" @click="completed_tasks">Completed</button>
        <button class="btn-select" id="pending"  @click="pending_tasks">Pending</button>
    </div>
    <div v-if="tasks" class="task-list">
        <TaskCard
            v-for="task in tasks"
            :key="task.id"
            :task="task"
            :isCompleted="isCompleted"
            :isPending="isPending"
            @completed="completed_task"
            @delete="delete_task"
         />
    </div>
    <div v-else>
        <h2> 🎉 No tasks left! Enjoy your free time. </h2>
    </div>
</template>

<script setup>
import { ref, watch } from 'vue';
import TaskCard from './TaskCard.vue';

const props = defineProps({
    tasks: {
        type: Array,
        required: true
    }
})
const emit = defineEmits(['completed_task', 'deleted_task'])
const completed_task = (task) =>{
    emit('completed_task', task)
}
const delete_task = (task) => {
    emit('deleted_task', task)
}
let isCompleted = ref(false)
const completed_tasks = () => {
    isCompleted.value = true
    isPending.value = false
}
let isPending = ref(false)
const pending_tasks = () => {
    isPending.value = true
    isCompleted.value = false
}
const all = () => {
    isCompleted.value = false
    isPending.value = false
}

</script>
<style lang="scss" scoped>
.task-list {
display: flex;
flex-wrap: wrap;
gap: 10px;
}
.select{
    display: flex;
    gap: 4px;
    padding-left: 18px;
    padding-top: 18px;
    padding-bottom: 18px;
}
.btn-select{
    border: none;
    border-radius: 8px;
    width: 100px;
    height: 30px;
    font-weight: bold;
}
#pending{
    color: white;
    background-color: green;
}
#complete{
    color: white;
    background-color: gray;
}
</style>
