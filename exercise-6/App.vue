<template>
  <div class="container">
    <h1>Todo App</h1>
    <TasksList :tasks="tasks" />
  </div>
</template>


<script>
import 'bootstrap/dist/css/bootstrap.css';
import TasksList from './components/TasksList';

export default {
  name: 'app',
  components: {
    TasksList,
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
</style>
