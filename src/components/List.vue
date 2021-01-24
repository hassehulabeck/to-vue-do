<template>
  <h1>Att göra</h1>
  <todo-form @add-todo="addTodo" />
  <section>
    <ul>
      <li v-for="item in todolist" :key="item.id">
        <ListItem :item="item" @is-done="isDone" />
      </li>
    </ul>
  </section>
</template>

<script>
import ListItem from "./ListItem.vue";
import TodoForm from "./TodoForm.vue";

export default {
  components: {
    ListItem,
    TodoForm,
  },
  name: "List",
  data() {
    return {
      todolist: [
        {
          id: 2,
          name: "Diska",
          needsToBeDone: true,
        },
        {
          id: 3,
          name: "Tvätta",
          needsToBeDone: true,
        },
        {
          id: 49,
          name: "Resa i tiden",
          needsToBeDone: false,
        },
      ],
    };
  },
  methods: {
    isDone(idx) {
      let index = this.todolist.findIndex((x) => x.id == idx);
      this.todolist[index].needsToBeDone = !this.todolist[index].needsToBeDone;
    },
    addTodo(task) {
      // get new id-number
      let lastId = this.todolist[this.todolist.length - 1].id;
      let newTask = {
        name: task,
        id: lastId + 1,
        needsToBeDone: true,
      };
      this.todolist.push(newTask);
    },
  },
};
</script>

<style scoped>
section {
  width: 100%;
}
ul {
  list-style-type: none;
  width: 50%;
  margin: 0 auto;
}
</style>
