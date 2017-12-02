<template>
  <ul class="list-group">
    <TaskItem v-for="task in tasks" :task="task" :key="task.id" />
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
  };
</script>
