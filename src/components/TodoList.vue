<template>
  <ul>
    <li v-for="(todoItem, index) in propsdata" :key="index">
      <div
        :class="{ doneTodo: todoItem.completed }"
        @click="toggleTodo(todoItem, index)"
      >
        <span class="checkIcon">
          <i class="fa fa-check" aria-hidden="true"></i>
        </span>
        {{ todoItem.item }}
      </div>
      <span
        class="removeBtn"
        type="button"
        @click="removeTodo(todoItem, index)"
      >
        <i class="fa fa-trash-o" aria-hidden="true"></i>
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
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}
li {
  width: 350px;
  height: 45px;
  line-height: 45px;
  display: flex;
  justify-content: space-between;
  background-color: #fff;
  margin: 7px 0px;
  padding: 0px 7px;
  border-radius: 2px;
  cursor: pointer;
}
.checkIcon {
  margin: 0px 7px;
  color: #42b883;
}
.removeBtn {
  margin-right: 7px;
  color: rgb(214, 94, 94);
  cursor: pointer;
}
.doneTodo {
  text-decoration: line-through;
  color: rgb(130, 130, 130);
}
</style>
