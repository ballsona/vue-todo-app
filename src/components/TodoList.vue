<template>
  <ul>
    <li v-for="(todoItem, index) in propsdata" :key="index">
      <span
        :class="{ doneTodo: todoItem.completed }"
        @click="toggleTodo(todoItem, index)"
      >
        {{ todoItem.item }}
      </span>
      <span
        class="removeBtn"
        type="button"
        @click="removeTodo(todoItem, index)"
      >
        삭제
      </span>
    </li>
  </ul>
</template>

<script lang="ts">
import type { TodoItem } from "@/App.vue";

export default {
  props: ["propsdata"],
  methods: {
    toggleTodo(todoItem: TodoItem, index: number) {
      this.$emit("toggleTodoItem", todoItem, index); // App의 toggleTodoItem 함수 호출
    },
    removeTodo(todoItem: string, index: number) {
      this.$emit("removeTodoItem", todoItem, index); // App의 removeTodoItem 함수 호출
    },
  },
};
</script>

<style>
ul {
  list-style-type: none;
  padding-left: 0;
  margin-top: 0;
  text-align: left;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}
li {
  width: 350px;
  height: 35px;
  line-height: 35px;
  display: flex;
  background-color: #fff;
  margin: 5px 0px;
  padding: 0px 7px;
  border-radius: 3px;
  cursor: pointer;
}
.removeBtn {
  margin-left: auto;
  color: rgb(195, 80, 80);
  font-size: 12px;
  cursor: pointer;
}
.doneTodo {
  text-decoration: line-through;
}
</style>
