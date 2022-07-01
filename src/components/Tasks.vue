<template>
  <!-- If no tasks available, display message -->
  <p v-if="!tasks.length">Enter a task!</p>
  <!-- loop over tasks array and display items on page -->
  <ul v-else v-for="task in tasks">
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
p {
  text-align: center;
  text-transform: capitalize;
}

li {
  list-style: none;
  width: 25%;
  margin: 0 auto;
  padding: 10px;
  position: relative;
  background-color: #e9ecef;
}

span {
  position: absolute;
  top: 10px;
  right: 10px;
  cursor: pointer;
  color: lightcoral;
  font-weight: bolder;
}
</style>
