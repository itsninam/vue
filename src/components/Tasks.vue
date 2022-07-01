<template>
  <h1>Task Tracker</h1>
  <!-- loop over tasks array and display items on page -->
  <ul v-for="task in tasks">
    <li @click="deleteTask(task.id)">
      <p>{{ task.task }}</p>
      <p>{{ task.date }}</p>
      <span>ⓧ</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  emits: ["delete-task"],
  methods: {
    deleteTask(id) {
      //emit function to app.vue
      this.$emit("delete-task", id);
    },
  },
};
</script>

<style></style>
