<template>
  <input
    type="text"
    v-model="newTodoItem"
    v-on:keyup.enter="addTodo"
    placeholder="add what you have to do"
  />
  <button v-on:click="addTodo">추가</button>
</template>

<script lang="ts">
export default {
  data() {
    return {
      newTodoItem: "",
    };
  },
  methods: {
    addTodo() {
      const value = this.newTodoItem;
      if (value) {
        localStorage.setItem(value, value);
        this.clearInput();
      }
    },
    clearInput() {
      this.newTodoItem = "";
    },
  },
};
</script>

<style>
input {
  width: 250px;
  height: 35px;
  background: #fff;
  border: none;
  border-radius: 5px;
  padding-left: 10px;
  margin-right: 10px;
  font-size: 1em;
}
input:focus {
  outline: none;
}
</style>
