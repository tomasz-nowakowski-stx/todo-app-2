<template>
  <div class="form">
    <div class="input-group">
      <input v-model="titleText" type="text" class="form-control">
      <span class="input-group-btn">
        <button @click="sendForm()" class="btn btn-default" type="button">
          <span class="glyphicon glyphicon-plus"></span> Add Task
        </button>
      </span>
    </div>
  </div>
</template>


<script>
  export default {
    data() {
      return {
        titleText: '',
      };
    },
    methods: {
      sendForm() {
        if (this.titleText.length > 0) {
          const title = this.titleText;
          this.$emit('add-task', {
            title,
            done: false,
          });
          this.titleText = '';
        }
        this.isCreating = false;
      },
    },
  };
</script>
