<template>
  <ul>
    <TodoItem
      v-for="(todo, index) in todos"
      :key="index"
      :todo="todo"
      :index="index"
      @del="del"
    />
  </ul>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  emits: ["del"],
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
  },
};
</script>
