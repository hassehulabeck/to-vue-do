<template>
  <div>
    <h1>Ekonomi</h1>
    <p>{{ totalCost }}</p>
  </div>
</template>

<script>
export default {
  name: "Economy",
  props: {
    totalCost: Number,
  },
};
</script>

<style scoped>
h1 {
  color: red;
  font-weight: 700;
}
div {
  border: thin solid black;
  margin: 1em;
}
</style>
