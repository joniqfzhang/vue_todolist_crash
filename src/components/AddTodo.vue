<template>
  <div>
    <form class="form" @submit.prevent="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo..." />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>
<script>
//import uuid from 'uuid';

export default {
  name: "AddTodo",
  data() {
    return {
      title: "test placeholder... ",
    };
  },
  methods: {
    addTodo(e) {
      //e.preventDefault();
      const newTodo = {
        //id: uuid(),//this uuid is not working?1
        title: this.title,
        completed: false,
      };
      // send to parent
      this.$emit("add-todo", newTodo);
      this.title = "";
    },
  },
};
</script>
<style scoped>
.form {
  display: flex;
}

.form input[type="text"] {
  flex: 10;
  padding: 5px;
}
.form input[type="submit"] {
  flex: 2;
}
</style>
