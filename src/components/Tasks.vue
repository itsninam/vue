<template>
  <!-- loop over tasks array and display items on page -->
  <ul v-for="task in tasks">
    <li>
      <p>{{ task.task }}</p>
      <p>{{ task.date }}</p>
      <span @click="deleteTask(task.id)">ⓧ</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  emits: ["delete-task", "submit-task"],
  methods: {
    deleteTask(id) {
      //emit function to app.vue
      this.$emit("delete-task", id);
    },
  },
};
</script>

<style scoped>
li {
  list-style: none;
  border: 1px solid lightsalmon;
  width: 25%;
  margin: 0 auto;
  padding: 10px;
  position: relative;
}

span {
  position: absolute;
  top: 10px;
  right: 10px;
  cursor: pointer;
  color: lightsalmon;
  font-weight: bolder;
}
</style>
