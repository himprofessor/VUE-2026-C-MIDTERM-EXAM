<template>
  <div class="main-app">
    <header>
      <h1>My Tasks</h1>
    </header>

    <TaskList
      :items="myList"
      @do-complete="finishTask"
      @do-remove="deleteTask"/>

  </div>
</template>

<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';

const myList = ref([
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

const finishTask = (id) => {
  const item = myList.value.find(t => t.id === id);
  if (item) {
    item.completed = true;
  }
};

const deleteTask = (id) => {
  myList.value = myList.value.filter(t => t.id !== id);
};
</script>


<!-- style  -->
<style lang="scss" scoped>
body{
  background: gray;
  font-family: sans-serif;
}

.main-app {
  max-width: 500px;
  margin: 30px auto;
  padding: 20px;
  background: white;
  border-radius: 5px;
}

hearder{
  text-align: center;
  margin-top: 20px;

}

</style>
