<template>
  <div class="clearAllBtn" @click="clearTodo">Clear All</div>
</template>

<script lang="ts">
export default {
  methods: {
    clearTodo() {
      localStorage.clear();
    },
  },
};
</script>

<style>
.clearAllBtn {
  color: #cb3939;
  display: black;
}
</style>
