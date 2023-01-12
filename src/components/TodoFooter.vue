<template>
  <div class="clearAllBtn" @click="removeAll">Clear All</div>
</template>

<script lang="ts">
export default {
  methods: {
    removeAll() {
      this.$emit("removeAll");
    },
  },
};
</script>

<style>
.clearAllBtn {
  color: #cb3939;
  display: black;
  cursor: pointer;
}
</style>
