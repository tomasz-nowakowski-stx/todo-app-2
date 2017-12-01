<template>
  <div class="container">
    <h1>Todo App</h1>
    <CreateTask class="create-task" @add-task="addTask" />
    <TasksList :tasks="tasks" />
  </div>
</template>


<script>
import 'bootstrap/dist/css/bootstrap.css';
import TasksList from './components/TasksList';
import CreateTask from './components/CreateTask';

export default {
  name: 'app',
  components: {
    TasksList,
    CreateTask,
  },
  methods: {
    addTask(task) {
      this.tasks.push(task);
    },
  },
  data() {
    return {
      tasks: [{
        id: 1,
        name: 'Learn Vue.js 2',
        done: false,
      }, {
        id: 2,
        name: 'Learn about Progressive Web Apps',
        done: true,
      }, {
        id: 3,
        name: 'Learn about Server-Side Rendering',
        done: false,
      }, {
        id: 4,
        name: 'Buy yourself a beer',
        done: false,
      }],
    };
  },
};
</script>


<style scoped>
  .container {
    width: 500px;
  }

  .create-task {
    margin-bottom: 10px;
  }
</style>
