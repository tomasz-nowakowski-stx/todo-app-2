<template>
  <ul class="list-group">
    <TaskItem v-for="task in tasks" :task="task" :key="task.id" @delete-task="deleteTask" />
  </ul>
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
    methods: {
      deleteTask(task) {
        const taskIndex = this.tasks.indexOf(task);
        this.tasks.splice(taskIndex, 1);
      },
    },
  };
</script>
