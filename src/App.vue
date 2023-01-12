<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput @addTodo="addTodo"></TodoInput>
    <TodoList
      v-bind:propsdata="todoItems"
      @removeTodo="removeTodo"
      @toggleTodo="toggleTodo"
    ></TodoList>
    <TodoFooter @removeAll="removeAll"></TodoFooter>
  </div>
</template>

<script lang="ts">
import TodoHeader from "./components/TodoHeader.vue";
import TodoFooter from "./components/TodoFooter.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    TodoHeader: TodoHeader,
    TodoFooter: TodoFooter,
    TodoInput: TodoInput,
    TodoList: TodoList,
  },
  data() {
    return {
      todoItems: [] as Array<string | null>,
    };
  },
  created() {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  methods: {
    addTodo(value: string) {
      if (value) {
        localStorage.setItem(value, value);
        this.todoItems.push(value);
      }
    },
    toggleTodo(todoItem: string) {
      console.log(todoItem);
    },
    removeTodo(todoItem: string, index: number) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    removeAll() {
      localStorage.clear();
      this.todoItems = [];
    },
  },
};
</script>

<style>
body {
  text-align: center;
  background-color: #e6e6e6;
}
</style>
