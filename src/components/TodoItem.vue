<template>
  <li>
    {{ todo }}
    <button @click="delTodo(index)">del</button>
  </li>
</template>

<script>
export default {
  emits: ["del"],
  props: {
    todo: String,
    index: Number,
  },
  methods: {
    delTodo(index) {
      this.$emit("del", index);
    },
  },
};
</script>
