<template>
  <header>
    <h1>{{title}}</h1>
    <Button
      v-on:button-click="this.$emit('toggle-add-task')"
      v-bind:color="showAddTask ? 'red' : 'green'"
      v-bind:text="showAddTask ? 'Close' : 'Add Task'"
    />
  </header>
</template>

<script>
import Button from "./Button";

export default {
  name: "Header",
  props: {
    title: String,
    showAddTask: Boolean
  },
  components: {
    Button
  }
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>