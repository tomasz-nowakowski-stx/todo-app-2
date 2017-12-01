<template>
  <li class="list-group-item">
    <span class="title">{{task.name}}</span>
    <span class="glyphicon glyphicon-ok" v-show="task.done"></span>
  </li>

</template>


<script>
  export default {
    props: {
      task: {
        type: Object,
        required: true,
      },
    },
  };
</script>
