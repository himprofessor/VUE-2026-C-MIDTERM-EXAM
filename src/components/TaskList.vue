<script setup>

import TaskCard from './TaskCard.vue';

const props = defineProps({
    tasks : Array
})

const emit = defineEmits(['show-empty' ])

function showEmpty(task){
    emit('show-empty', task)
}

function buttonClick(task){
    emit('button-click', task)
}

function handlesComplete(){
    emit ('complete-task', task)
}
function deleteTask(id){
    emit ('delete-task', id)
}

</script>

<template>
    <div>
        <TaskCard
            v-for = "task in tasks "
            :key="task.id"
            :task="task"
            @show-empty="showEmpty"
            @button-click="buttonClick"
            @complete-task="handlesComplete"
            @delete-task="deleteTask"
        />
    </div>
</template>

<style scoped>

</style>