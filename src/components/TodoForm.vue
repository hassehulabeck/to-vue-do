<template>
  <form @submit.prevent>
    <label for="task">Task</label>
    <input type="text" v-model.trim="newTask.name" />
    <label for="cost">Cost</label>
    <input type="number" v-model.trim="newTask.cost" />
    <button @click="createTask">Create task</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTask: {
        name: "",
        cost: null,
      },
    };
  },
  name: "TodoForm",
  methods: {
    createTask() {
      if (this.newTask.name !== "") {
        this.$emit("addTodo", this.newTask);
        this.clearInput();
      }
    },
    clearInput() {
      this.newTask.name = "";
      this.newTask.cost = 0;
    },
  },
};
</script>

<style>
label {
  display: block;
}
</style>
