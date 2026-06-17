<template>
    <div class="app">

        <div class="action-group">
        <input v-model="NewTask" placeholder="Add Task">
        <button @click="addtask">Add Task</button>
        </div>
      
        <ul>
            <li v-for ="(task, index) in tasks" :key="index">
                <span class="task-info">[{{ index }}]</span>
            </li>
                <template v-if="editingIndex === index">
                    <input v-model="editingText" placeholder="Update Task">
                    <button @click="updateTask(index)">Update</button>
                    <button @click="cancelEdit">Cancel</button>
                </template>

                <template v-else>
                    <span class="task-text">{{ task }}</span>
                    <button @click="startEdit(index, task)">Edit</button>
                    <button @click="deleteTask(index)">Delete</button>
            </template>
    </ul>
    </div>
</template>

<script>
import { ref } from 'vue';

 
const NewTask = ref('');
const editingIndex = ref(-1);
const editingText = ref('');
const tasks = ref(['2 pending', '1 completed',]);
    
const addtask = () => {
    if (NewTask.value.trim() !== '') {
        tasks.value.push(NewTask.value.trim());
        NewTask.value = '';
    }
};

const deleteTask = (index) => {
    tasks.value.splice(index, 1);
    if (editingIndex.value === index) {
        cancelEdit();
    }
};
const updateTask = (index) => {
    if (editingText.value.trim() !== '') {
        tasks.value[index] = editingText.value.trim();
        cancelEdit();
    }
};

const startEdit = (index, taskText) => {
    editingIndex.value = index;
    editingText.value = taskText;
};
const cancelEdit = () => {
    editingIndex.value = -1;
    editingText.value = '';
};
</script>

<style scoped>
.app {
    padding: 20px;
    input {
        margin-right: 5px;
        padding: 5px;
    }
    button {
        margin-right: 15px;
        padding: 5px 10px;
    }
    ul {
        padding-left: 10px;
        margin-top: 20;
    }
    li {
        margin-bottom: 10px;
        display: flex;
        align-items: center;
}
.task-info {
        margin-right: 10px;
        color: #666;
}
.task-text {
        margin-right: 15px;
        min-width: 150px;
}
}
</style>