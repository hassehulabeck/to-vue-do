<template>
  <div v-if="item.needsToBeDone">
    {{ item.name }}
    <button @click="isDone(item.id)">x</button>
  </div>
  <div v-else class="isDone">
    {{ item.name }}
  </div>
</template>

<script>
export default {
  name: "ListItem",
  props: {
    item: Object,
  },
  methods: {
    isDone(item) {
      this.$emit("isDone", item);
    },
  },
};
</script>

<style scoped>
div {
  background: #eeffaa;
  margin: 1em;
  padding: 3px;
}
.isDone {
  text-decoration-line: line-through;
  background: #eecc88;
}
button {
  border: none;
  background: orangered;
}
</style>
