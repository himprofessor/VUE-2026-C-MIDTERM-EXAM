<script setup>


import BaseCard from "./BaseCard.vue"


defineProps({

    task: Object

})


const emit = defineEmits([

    "status",

    "delete"

])



</script>



<template>
    
   
    <BaseCard>
       
        <h2>
            {{ task.title }}
        </h2>

        <p >Status: {{ task.completed ? 'Completed' : 'Pending' }}</p>

        <div class="btn" >
            <button  v-if="task.completed == false" @click="$emit('status', task.id)" id="com">
            Complete
        </button>

        <button @click="emit('delete', task.id)" id="del">

            Delete

        </button>
        </div>
    </BaseCard>


</template>