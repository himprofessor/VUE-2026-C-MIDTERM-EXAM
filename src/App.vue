<script setup>
  import { ref } from 'vue';
  import TaskList from './components/TaskList.vue';


  const tasks = ref ([
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
  ]);

  const removeTask = (id) => {
    tasks.value = tasks.value.filter(task => task.id !== id);
  };


 

</script>

<template>
  <div class="card">
    <h1>My Tasks</h1>
    <hr>
      <TaskList
        :tasks="tasks"
        @delete-task="removeTask"
      />
    </div>
</template>

<style scoped>
.card{
    width: 100%;
    max-width: 800px;
    border: 1px solid #2a2a4a;
    border-radius: 20px;
    padding: 30px;
}
</style>
