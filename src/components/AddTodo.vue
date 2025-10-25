<template>
  <div class="form">
    <input type="text" id="newTodo" name="newTodo" v-model="todo" />
    <button class="addButton" @click="add">Add</button>
  </div>
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

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 5px;
  width: 400px;
}

.addButton {
  color: white;
  background-color: black;
  padding: 3px;
}
</style>
