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
  margin-top: 10px;
  gap: 5px;
  width: 400px;
}

input {
  border: 1px solid gray;
  font-size: 15px;
  padding: 0 5px;
}

input,
.addButton {
  height: 35px;
  box-sizing: border-box;
  border-radius: 4px;
  font-family: "Archivo", sans-serif;
  font-optical-sizing: auto;
  font-weight: 600;
  font-style: normal;
}

.addButton {
  color: white;
  background-color: black;
  padding: 3px;
  border: none;
}
</style>
