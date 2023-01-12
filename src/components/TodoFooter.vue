<template>
  <div class="clearAllBtn" @click="removeAll">Clear All</div>
</template>

<script lang="ts">
export default {
  methods: {
    removeAll() {
      this.$emit("removeAll"); // 부모 컴포넌트의 removeAll 함수를 호출
    },
  },
};
</script>

<style>
.clearAllBtn {
  color: rgb(214, 94, 94);
  font-weight: 500;
  font-size: 1em;
  cursor: pointer;
}
</style>
