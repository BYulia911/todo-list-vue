<template>
  <div id="app">
    <h1>To-Do List</h1>
    <h2>What needs to be done?</h2>
    <AddTodo @add="addTodo" />
    <p>
      <span style="color: red">count</span> out of {{ this.todos.length }} items
      completed
    </p>
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
      if (str) {
        this.todos.push(str);
      }
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

<style>
@import url("https://fonts.googleapis.com/css2?family=Archivo:ital,wght@0,100..900;1,100..900&display=swap");

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: "Archivo", sans-serif;
  font-optical-sizing: auto;
  font-weight: 500;
  font-style: normal;
}

h1,
h2 {
  color: #1c1c1c;
  margin: 5px;
}
</style>
