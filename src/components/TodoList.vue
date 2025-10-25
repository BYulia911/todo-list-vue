<template>
  <ul>
    <TodoItem
      v-for="(todo, index) in todos"
      :key="index"
      :todo="todo"
      :index="index"
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
    save(index, str) {
      this.$emit("save", index, str);
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
