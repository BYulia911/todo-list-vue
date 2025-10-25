<template>
  <input type="text" v-model="todo" />
  <button @click="add">create</button>
</template>

<script>
export default {
  emits: ["add"],
  methods: {
    add() {
      this.$emit("add", this.todo);
      this.todo = "";
    },
  },
  data() {
    return {
      todo: "",
    };
  },
};
</script>
