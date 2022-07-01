<template>
  <h1>Task Tracker</h1>
  <div class="wrapper">
    <UserInput @submit-task="addTask" />
    <Tasks :tasks="tasks" @delete-task="deleteTask" />
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";
import UserInput from "./components/UserInput.vue";

export default {
  name: "App",
  components: {
    Tasks,
    UserInput,
  },
  //remove each task on click
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
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
        date: "2022-06-10",
        reminder: true,
      },
      {
        id: 2,
        task: "Doctor's Appointment",
        date: "2022-06-25",
        reminder: true,
      },
      {
        id: 3,
        task: "Pay Bills",
        date: "2022-06-20",
        reminder: false,
      },
    ];
  },
};
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
}
.wrapper {
  max-width: 1200px;
  width: 85%;
  margin: 0 auto;
}

h1 {
  text-align: center;
}

form {
  text-align: center;
}

input {
  text-transform: capitalize;
}
</style>
