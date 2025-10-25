<template>
  <div id="app">
    <h1>To-Do List</h1>
    <h2>What needs to be done?</h2>
    <AddTodo @add="addTodo" />
    <TodoList :todos="todos" @del="delTodo" @save="saveTodo" />
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "app",
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
    saveTodo(index, str) {
      this.todos[index] = str;
    },
  },
};
</script>

<style scoped>
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1,
h2 {
  color: rgb(60, 60, 60);
  margin: 5px;
}
</style>
