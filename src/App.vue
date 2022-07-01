<template>
  <div class="wrapper">
    <Tasks :tasks="tasks" @delete-task="deleteTask" />
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";

export default {
  name: "App",
  components: {
    Tasks,
  },
  //remove each task on click
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
  data() {
    return {
      //creating tasks array
      tasks: [],
    };
  },

  //this is where API call would go
  created() {
    //passing tasks objects into tasks array
    this.tasks = [
      {
        id: 1,
        task: "Grocery Shopping",
        date: "July 5, 2022",
        reminder: true,
      },
      {
        id: 2,
        task: "Doctor's Appointment",
        date: "July 10, 2022",
        reminder: true,
      },
      {
        id: 3,
        task: "Pay Bills",
        date: "July 20, 2022",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
.wrapper {
  max-width: 1200px;
  width: 85%;
  margin: 0 auto;
}
</style>
