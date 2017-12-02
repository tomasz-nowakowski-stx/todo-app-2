<template>
  <li class="list-group-item" :class="{completed: task.done}">
    <div v-if="!isEditing">
      <span class="name">{{task.name}}</span>
      <div class="pull-right">
        <button class="btn btn-primary btn-xs" @click="completeTask()">
          <span class="glyphicon glyphicon-remove" v-show="task.done"></span>
          <span class="glyphicon glyphicon-ok" v-show="!task.done"></span>
        </button>
        <button class="btn btn-default btn-xs" @click="showForm()">
          <span class="glyphicon glyphicon-pencil"></span>
        </button>
        <button class="btn btn-danger btn-xs" @click="deleteTask()">
          <span class="glyphicon glyphicon-trash"></span>
        </button>
      </div>
    </div>
    <div class="form" v-if="isEditing">
      <div class="input-group">
        <input v-model="task.name" type="text" class="form-control">
        <span class="input-group-btn">
        <button @click="hideForm" class="btn btn-default" type="button">
          <span class="glyphicon glyphicon-remove"></span> Close
        </button>
      </span>
      </div>
    </div>
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
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
      deleteTask() {
        this.$emit('delete-task', this.task);
      },
      completeTask() {
        this.task.done = !this.task.done;
      },
    },
  };
</script>


<style scoped>
  .completed {
    background: #e0f4ec;
  }

  .completed .name {
    color: #37893a;
    text-decoration: line-through;
  }
</style>
