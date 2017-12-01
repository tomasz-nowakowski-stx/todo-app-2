<template>
  <ul class="list-group">
    <li class="list-group-item" v-for="task in tasks" :key="task.id">
      <span class="title">{{task.name}}</span>
      <span class="glyphicon glyphicon-ok" v-show="task.done"></span>
    </li>
  </ul>
</template>

<script>
  export default {
    props: {
      tasks: {
        type: Array,
        required: true,
      },
    },
  };
</script>
