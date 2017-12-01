<template>
  <li class="list-group-item" :class="{completed: task.done}">
    <div v-if="!isEditing">
      <span class="title">{{task.title}}</span>
      <div class="pull-right">
        <button class="btn btn-primary btn-xs" v-show="task.done" @click="completeTask()">
          <span class="glyphicon glyphicon-remove"></span>
        </button>
        <button class="btn btn-primary btn-xs" v-show="!task.done" @click="completeTask()">
          <span class="glyphicon glyphicon-ok"></span>
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
        <input v-model="task.title" type="text" class="form-control">
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
        this.$emit('complete-task', this.task);
      },
    },
  };
</script>


<style scoped>
  .completed {
    background: #e0f4ec;
  }

  .completed .title {
    color: #37893a;
    text-decoration: line-through;
  }
</style>
