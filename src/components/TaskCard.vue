<template>
    <BaseCard>
        <div v-if="isCompleted" v-for="value in completed_tasks">
            <h3 >{{ value.title }}</h3>
            <p style="color: grey;">status: Completed</p>
            <button @click="completedTask">Complete</button>
            <button @click="delete_task">Delete</button>
        </div>
        <div v-else-if="isPending" v-for="value in pending_tasks">
            <h3 >{{ value.title }}</h3>
            <p style="color: green;">status: Pending</p>
            <button @click="completedTask">Complete</button>
            <button @click="delete_task">Delete</button>
        </div>
        <div v-else>
            <h3>{{ task.title }}</h3>
            <p style="color: gray;" v-if="task.completed">status: Completed</p>
            <p  style="color: green;" v-else>status: Pending</p>
            <button @click="completedTask">Complete</button>
            <button @click="delete_task">Delete</button>
        </div>
    </BaseCard>
    <div v-if="showAlert" class="alert-box">
        <p>Are you sure!</p>
        <p>Click ok if you want to delete this task</p>
        <button @click="dismissAlert">cancel</button>
        <button @click="send_data">Ok</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import BaseCard from './BaseCard.vue';
const props = defineProps({
    task: {
        type: Object,
        required: true
    },
    isCompleted: {
        type: Boolean,
        required: true
    },
    isPending: {
        type: Boolean,
        required: true
    }
})

const emit = defineEmits(['completed', 'delete'])
const completedTask = () => {
    emit('completed', props.task)
}
const delete_task = () => {
    showAlert.value = true
}
const send_data = () => {
    emit('delete', props.task)
}
const showAlert = ref()
const dismissAlert = () => {
    showAlert.value = false
}
const data = ref([props.task])
let completed_tasks = ref([])
let pending_tasks = ref([])
data.value.forEach(item => {
    if(item.completed === true){
        completed_tasks.value.push(item)
    }else{
        pending_tasks.value.push(item)
    }
});

</script>

<style lang="scss" scoped>
.alert-box {
    padding: 15px;
    background-color: #ffdde1;
    border: 1px solid #ff4a5a;
    margin-bottom: 10px;
}
</style>