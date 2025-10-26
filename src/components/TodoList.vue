<template>
  <ul>
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @del="del"
      @save="save"
    />
  </ul>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  emits: ["del", "save"],
  components: {
    TodoItem,
  },
  props: {
    todos: Array,
  },
  methods: {
    del(index) {
      this.$emit("del", index);
    },
    save(index, str, status) {
      this.$emit("save", index, str, status);
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
</style>
