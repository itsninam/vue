<template>
  <header class="wrapper">
    <h1>Task Tracker</h1>
    <button @click="onToggleTask">
      {{ showAddTask ? "Close" : "Add Task" }}
    </button>
  </header>
  <main class="wrapper">
    <!-- v-if directive to hide input form on page load -->
    <div v-if="showAddTask">
      <UserInput @submit-task="addTask" />
    </div>
    <Tasks :tasks="tasks" @delete-task="deleteTask" />
  </main>
  <footer>
    <p>Created by Madalina</p>
  </footer>
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
    onToggleTask() {
      this.showAddTask = !this.showAddTask;
    },
  },
  data() {
    return {
      //creating tasks array
      tasks: [],
      showAddTask: false,
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
html {
  position: relative;
  height: 100%;
}

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
  margin-right: 15px;
}

header {
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  background-color: lightcoral;
  border: none;
  padding: 10px 15px;
  border-radius: 5px;
  color: #fff;
  cursor: pointer;
}

form {
  text-align: center;
}

input {
  text-transform: capitalize;
  padding: 5px;
  width: 16%;
  margin-left: 10px;
}

footer {
  text-align: center;
  position: absolute;
  bottom: 0;
}
</style>
