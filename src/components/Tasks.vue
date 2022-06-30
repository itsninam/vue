<template>
  <h1>Task Tracker</h1>
  <!-- loop over tasks array and display items on page -->
  <ul v-for="task in tasks">
    <li>
      <p>{{ task.task }}</p>
      <p>{{ task.date }}</p>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
};
</script>

<style></style>
