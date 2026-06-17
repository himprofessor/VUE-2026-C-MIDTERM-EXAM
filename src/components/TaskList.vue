<script setup>


import TaskCard from "./TaskCard.vue"



const props = defineProps({

    tasks: Array

})


const emit = defineEmits([

    "status-task",

    "delete-task"

])



function statusTask(task) {

    emit(
        "status-task",
        task
    )

}




function removeTask(id) {

    emit(
        "delete-task",
        id
    )

}



</script>



<template>
    <div v-if="tasks.length ===0" id="not">
       <p>🎉 No tasks left!                   
      Enjoy your free time.</p>
    </div>

    <div>
        <TaskCard v-for="task in tasks" :key="task.id" :task="task" @status="statusTask"
            @delete="removeTask " />
    </div>


</template>