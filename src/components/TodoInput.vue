<template>
  <input
    type="text"
    v-model="newTodoItem"
    @keyup.enter="addTodo"
    placeholder="add what you have to do"
  />
  <button @click="addTodo">추가</button>
</template>

<script lang="ts">
export default {
  data() {
    return {
      newTodoItem: "",
    };
  },
  methods: {
    // todo를 새로 추가하는 함수
    addTodo() {
      if (this.newTodoItem) {
        this.$emit("addTodoItem", this.newTodoItem); // 부모 컴포넌트(App) 의 addTodo 함수 호출
        this.clearInput();
      }
    },
    // input value 제거하는 함수
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
