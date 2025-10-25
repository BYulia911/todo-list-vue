<template>
  <li>
    <div class="inputs">
      <input
        class="checkbox-input"
        type="checkbox"
        name="done"
        id="done"
        v-model="checked"
      />
      <input
        v-if="isDisabled"
        v-model="todoInput"
        id="todoInput"
        name="todoInput"
      />
      <span v-else :class="{ checked: checked }">{{ todo }}</span>
    </div>
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
      checked: false,
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
input,
button {
  font-family: "Archivo", sans-serif;
  font-optical-sizing: auto;
  font-weight: 800;
  font-style: normal;
}

li {
  display: flex;
  flex-direction: column;
  margin: 0 0 30px 0;
  gap: 5px;
}

.inputs {
  display: flex;
  width: 100%;
  flex-direction: row;
  align-items: center;
  gap: 10px;
}

input {
  width: calc(100% - 40px);
  height: 30px;
  font-size: 18px;
  font-weight: 500;
  box-sizing: border-box;
}

span {
  font-size: 18px;
  margin-left: 4px;
}

.checkbox-input {
  appearance: none;
  width: 30px;
  height: 30px;
  border-radius: 4px;
  border: 1px solid black;
  background-color: #fff;
  margin: 0;
}

.checkbox-input:checked {
  background-color: #ff4f4f;
  border-color: #ff4f4f;
  background-image: var(--itc-checkbox-bg-image);
  --itc-checkbox-bg-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 20 20'%3e%3cpath fill='none' stroke='%23fff' stroke-linecap='round' stroke-linejoin='round' stroke-width='3' d='m6 10 3 3 6-6'/%3e%3c/svg%3e");
}

.buttons {
  display: flex;
  flex-direction: row;
  gap: 5px;
}

button {
  width: 150px;
  height: 30px;
  border: none;
  padding: 4px 0;
  border-radius: 4px;
}

#editBtn {
  color: black;
  background-color: white;
  border: 1px solid black;
}

#delBtn {
  color: white;
  background-color: #f00202;
}

.checked {
  color: gray;
  text-decoration: line-through;
}
</style>
