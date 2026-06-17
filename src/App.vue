  <template>
    <div class="container">
      <TaskList 
      :tasks="tasks"
      :taskCount="taskCount" 
      @complete-task="completeTask" 
      @delete-task="deleteTask" />
    </div>
  </template>

<script setup>
import { computed, ref } from 'vue'
import TaskList from './compoments/TaskList.vue';

const tasks = ref([
  {
    id: 1,
    title: "Finish Vue homework",
    completed: false
  },
  {
    id: 2,
    title: "Buy groceries",
    completed: true
  },
  {
    id: 3,
    title: "Call the dentist",
    completed: false
  },
  {
    id: 4,
    title: "Read one chapter of a book",
    completed: false
  }
])

const selectedTask = ref(null)

const taskCount = computed(() => {
  return tasks.value.filter(task => !task.completed).length
})

const completeTask = (taskObject) => {
  tasks.value = tasks.value.filter(task => task.id !== taskObject.id)
  if (selectedTask.value?.id === taskObject.id) {
    selectedTask.value = null
  }
}

const deleteTask = (taskId) => {
  tasks.value = tasks.value.filter(task => task.id !== taskId)
  if (selectedTask.value?.id === taskId) {
    selectedTask.value = null
  }
}

</script>


<style scoped>
.container {
  width: 70%;
  max-width: 1200px;
  margin: 20px auto;
  display: flex;
  flex-direction: column;
  border: 1px solid #ddd;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  gap: 20px
}
</style>
