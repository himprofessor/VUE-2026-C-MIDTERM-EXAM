<template>
  <div id="app">
    <!-- Header & Task Count -->
    <div class="header">
      <h2>My Tasks</h2>
      <p v-if="tasks.length > 1" >You have 3 tasks today</p>
      <p v-else-if="tasks.length === 1" >You have {{ tasks.length }} tasks today</p>
      
    </div>

    <!-- Empty State -->
    <div v-if="tasks.length === 0" class="empty-state">
         No tasks left!<br>Enjoy your free time.
    </div>

    <!-- Task List -->
    <div v-else class="task-list">
      <TaskCard 
        v-for="task in tasks" 
        :key="task.id" 
        :task="task" 
        @complete-task="completeTask(task.id)" 
        @delete-task="deleteTask(task.id)" 
      />
    </div>
  </div>
</template>


<script>
import TaskCard from './components/TaskCard.vue';

export default {
  name: 'App',
  components: { TaskCard },
  data() {
    return {
      tasks: [
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
      ]
    };
  },
  methods: {
    completeTask(taskId) {
      const task = this.tasks.find(t => t.id === taskId);
      if (task) task.completed = true;
      
    },
    deleteTask(taskId) {
      this.tasks = this.tasks.filter(t => t.id !== taskId);
    }
  }
};
</script>

<style scoped>
#app {
  max-width: 500px;
  margin: 0 auto;
  font-family: sans-serif;
  background-color: #f7f9fc;
  padding: 20px;
  border-radius: 8px;
}
h2 {
  text-align: center;
  font-size: 40px;
  color: rgb(130, 130, 232);
  font-weight: bold;
}
.empty-state {
  text-align: center;
  padding: 40px 20px;
  color: #64748b;
  font-size: 1.2rem;
  background: #ffffff;
  border-radius: 6px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}
</style>
