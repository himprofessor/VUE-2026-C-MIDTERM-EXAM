<script setup>
import TaskCard from './TaskCard.vue';

defineProps({
    tasks: Array
})
const emit = defineEmits([
    "complete-task",
    "delete-task",
])


const deleteTask = (id) => {
    emit ('delete-task',id)
}

</script>

<template>
    <header class="head"">
        <h1>This is my tasks</h1>
        <p>You have {{ tasks.length }} tasks today</p>

    </header>
    <div class="task-card" v-if="tasks.length >0">
        <TaskCard v-for="task in tasks" :key="task.id" :task="task" @complete-task="completeTask" @delete-task="deleteTask"/>
    </div>
    <div class="no-task" v-else>
        <p >No tasks left!</p>
        <p>Enjoy your free time.</p>
    </div>
</template>



<style scoped>
.head {
    height: 120px;
    width: auto;
    padding-left: 40px;
    background: #01a99e85 ;
    border-radius: 24px 24px 0 0 ;
    

}
.head p{
    font-weight: bold;
}

.task-card {
    height: auto;
    width: auto;
    display: flex;
    flex-direction: column;


}

.no-task {
    height: auto;
    width: auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-top: 1px solid #000;
    background-color: #f9931f36;
}
</style>