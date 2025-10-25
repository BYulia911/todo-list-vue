<template>
  <AddTodo @add="addTodo" />
  <TodoList :todos="todos" @del="delTodo" />
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    TodoList,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(str) {
      this.todos.push(str);
    },
    delTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style></style>
