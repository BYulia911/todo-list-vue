<template>
  <li>
    <div v-if="isDisabled">
      <input v-model="todoInput" id="todoInput" name="todoInput" />
    </div>
    <span v-else>{{ todo }}</span>
    <div class="buttons">
      <button id="editBtn" @click="editTodo">
        {{ isDisabled ? "Save" : "Edit" }}
      </button>
      <button id="delBtn" @click="delTodo(index)">Delete</button>
    </div>
  </li>
</template>

<script>
export default {
  emits: ["del", "save"],
  data() {
    return {
      isDisabled: false,
      todoInput: this.todo,
    };
  },
  props: {
    todo: String,
    index: Number,
  },
  methods: {
    delTodo(index) {
      this.$emit("del", index);
    },
    editTodo() {
      this.isDisabled ? this.saveTodo() : (this.isDisabled = true);
    },
    saveTodo() {
      this.isDisabled = false;
      this.$emit("save", this.index, this.todoInput);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  flex-direction: column;
  margin: 10px;
  gap: 5px;
}

input {
  width: 100%;
  height: 30px;
  font-size: 14px;
  box-sizing: border-box;
}

span {
  font-size: 20px;
}

.buttons {
  display: flex;
  flex-direction: row;
  gap: 5px;
}

button {
  width: 150px;
  border: none;
  padding: 4px 0;
}

#editBtn {
  color: black;
  background-color: white;
  border: 1px solid black;
}

#delBtn {
  color: white;
  background-color: red;
}
</style>
