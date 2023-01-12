<template>
  <ul>
    <li v-for="(todoItem, index) in todoItems" :key="index">
      {{ todoItem }}
      <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)"
        >삭제</span
      >
    </li>
  </ul>
</template>

<script lang="ts">
export default {
  data() {
    return {
      todoItems: [],
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
    removeTodo(todoItem: [string], index: number) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
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
}
.removeBtn {
  margin-left: auto;
  color: rgb(195, 80, 80);
  font-size: 12px;
  cursor: pointer;
}
</style>
