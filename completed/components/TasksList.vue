<template>
  <div>
    <p>Completed Tasks: {{completedTasks.length}}</p>
    <ul class="list-group">
      <TaskItem v-for="task in tasks" :task="task" :key="task.id" @delete-task="deleteTask" @complete-task="completeTask"/>
    </ul>
  </div>
</template>

<script>
  import TaskItem from './TaskItem';

  export default {
    components: {
      TaskItem,
    },
    props: {
      tasks: {
        type: Array,
        required: true,
      },
    },
    computed: {
      completedTasks: function () {
        return this.tasks.filter(task => task.done === true);
      },
    },
    methods: {
      deleteTask(task) {
        console.log(task);
        const taskIndex = this.tasks.indexOf(task);
        this.tasks.splice(taskIndex, 1);
      },
      completeTask(task) {
        const taskIndex = this.tasks.indexOf(task);
        this.tasks[taskIndex].done = !this.tasks[taskIndex].done;
      },
    },
  };
</script>
