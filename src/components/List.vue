<template>
  <h1>Att göra</h1>
  <todo-form @add-todo="addTodo" />
  <Economy :totalCost="totalCost" />
  <section>
    <ul>
      <li v-for="item in todolist" :key="item.id">
        <ListItem :item="item" @is-done="isDone" />
      </li>
    </ul>
  </section>
</template>

<script>
import Economy from "./Economy.vue";
import ListItem from "./ListItem.vue";
import TodoForm from "./TodoForm.vue";

export default {
  components: {
    ListItem,
    TodoForm,
    Economy,
  },
  name: "List",
  data() {
    return {
      todolist: [
        {
          id: 2,
          name: "Diska",
          needsToBeDone: true,
          cost: 25,
        },
        {
          id: 3,
          name: "Tvätta",
          needsToBeDone: true,
          cost: 40,
        },
        {
          id: 49,
          name: "Resa i tiden",
          needsToBeDone: false,
          cost: 125,
        },
      ],
    };
  },
  computed: {
    totalCost: function () {
      return this.todolist.reduce((acc, item) => {
        if (item.needsToBeDone) {
          return acc + item.cost;
        } else {
          return acc;
        }
      }, 0);
    },
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
        name: task.name,
        id: lastId + 1,
        needsToBeDone: true,
        cost: Number(task.cost), // Utan number är det ett strängvärde som kommer från input...
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
