<template>
  <li class="list-group-item">
    <div v-if="!isEditing">
      <span class="name">{{task.name}}</span>
      <span class="glyphicon glyphicon-ok" v-show="task.done"></span>
      <div class="pull-right">
        <button class="btn btn-default btn-xs" @click="showForm()">
          <span class="glyphicon glyphicon-pencil"></span>
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
    },
  };
</script>
