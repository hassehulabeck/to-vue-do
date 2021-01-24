<template>
  <form @submit.prevent>
    <label for="task">Task</label>
    <input type="text" v-model.trim="newTask" />
    <button @click="createTask">Create task</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
    };
  },
  name: "TodoForm",
  methods: {
    createTask() {
      if (this.newTask !== "") {
        this.$emit("addTodo", this.newTask);
        this.clearInput();
      }
    },
    clearInput() {
      this.newTask = "";
    },
  },
};
</script>
