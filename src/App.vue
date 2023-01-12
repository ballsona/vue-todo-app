<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput @addTodoItem="addTodoItem"></TodoInput>
    <TodoList
      :propsdata="todoItems"
      @removeTodoItem="removeTodoItem"
      @toggleTodoItem="toggleTodoItem"
    ></TodoList>
    <TodoFooter @removeAll="removeAll"></TodoFooter>
  </div>
</template>

<script lang="ts">
import TodoHeader from "./components/TodoHeader.vue";
import TodoFooter from "./components/TodoFooter.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";

export interface TodoItem {
  completed: boolean;
  item: string;
}

export default {
  components: {
    TodoHeader: TodoHeader,
    TodoFooter: TodoFooter,
    TodoInput: TodoInput,
    TodoList: TodoList,
  },
  data() {
    return {
      todoItems: [] as Array<TodoItem>,
    };
  },
  created() {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        this.todoItems.push(
          JSON.parse(localStorage.getItem(localStorage.key(i)))
        );
      }
    }
  },
  methods: {
    // todo를 추가하는 함수
    addTodoItem(value: string) {
      if (value) {
        const newTodoObj = { completed: false, item: value };
        localStorage.setItem(value, JSON.stringify(newTodoObj));
        this.todoItems.push(newTodoObj);
      }
    },
    // todo 완료 여부를 체크하는 함수
    toggleTodoItem(todoItem: TodoItem, index: number) {
      this.todoItems[index].completed = !this.todoItems[index].completed;
      // localStorage 데이터를 업데이트
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    },
    // todo 삭제하는 함수
    removeTodoItem(todoItem: TodoItem, index: number) {
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index, 1);
    },
    // 모든 todo를 삭제하는 함수
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
  background-color: #242424;
}
</style>
