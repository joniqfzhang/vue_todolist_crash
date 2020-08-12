<template>
  <div class="todo-Item" v-bind:class="{'is-completed': dataTodo.completed}">
    <p>
      <input type="checkbox" v-on:change="markCompleted()" />
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  data() {
    return {
      dataTodo: this.todo,
    };
  },
  methods: {
    markCompleted() {
      this.dataTodo.completed = !this.dataTodo.completed;
    },
  },
};
</script>

<style scoped>
.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
.todo-Item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}
.is-completed {
  text-decoration: line-through;
}
</style>