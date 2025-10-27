<template>
  <div id="app">
    <h1>To-Do List</h1>
    <h2>What needs to be done?</h2>
    <AddTodo @add="addTodo" />
    <p>
      <span style="color: red">{{ completedTodos }}</span> out of
      {{ this.todos.length }} items completed
    </p>
    <FilterTodos @filter="filterChange" />
    <TodoList :todos="filteredTodos" @del="delTodo" @save="saveTodo" />
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
import FilterTodos from "./components/FilterTodos.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "app",
  components: {
    TodoList,
    AddTodo,
    FilterTodos,
  },
  data() {
    return {
      todos: JSON.parse(localStorage.getItem("todos")) || [],
      currentFilter: "",
    };
  },
  computed: {
    completedTodos() {
      return this.todos.filter((t) => t.completed).length;
    },
    filteredTodos() {
      if (this.currentFilter === "Completed") {
        return this.todos.filter((t) => t.completed);
      } else if (this.currentFilter === "Not completed") {
        return this.todos.filter((t) => t.completed === false);
      }
      return this.todos;
    },
  },
  methods: {
    addTodo(str) {
      if (str) {
        const newTodo = {
          id: Date.now(),
          name: str,
          completed: false,
        };
        this.todos.push(newTodo);
        this.updateLocalStorage();
      }
    },
    filterChange(filter) {
      this.currentFilter = filter;
    },
    delTodo(id) {
      const todo = this.todos.findIndex((t) => t.id === id);
      if (todo !== -1) {
        this.todos.splice(todo, 1);
        this.updateLocalStorage();
      }
    },
    saveTodo(id, str, status) {
      const todo = this.todos.find((t) => t.id == id);
      if (todo) {
        todo.name = str;
        todo.completed = status;
        this.updateLocalStorage();
      }
    },
    updateLocalStorage() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
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

h1 {
  margin-top: 20px;
}
</style>
