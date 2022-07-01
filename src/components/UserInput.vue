<template>
  <div></div>
  <form action="" @submit="onSubmit">
    <div>
      <label for="task">Enter task</label>
      <input
        type="text"
        id="task"
        name="task"
        placeholder="Enter task"
        v-model="task"
      />
    </div>

    <div>
      <label for="date">Enter date</label>
      <!-- two-way data binding w/ v-model -->
      <input
        type="date"
        id="date"
        name="date"
        placeholder="Enter date"
        v-model="date"
      />
    </div>

    <button>Submit</button>
  </form>
</template>
<script>
export default {
  name: "UserInput",
  data() {
    return {
      task: "",
      date: "",
    };
  },
  methods: {
    onSubmit(event) {
      //form validation
      event.preventDefault();
      if (!this.task) {
        return alert("Please enter a task");
      }

      //create new task object with user input
      const newTask = {
        id: Math.floor(Math.random() * 1000),
        task: this.task,
        date: this.date.toLocaleString(),
      };

      //clear form
      this.task = "";
      this.date = "";

      //emit new task object to App.vue component
      this.$emit("submit-task", newTask);
    },
  },
};
</script>
<style scoped>
div {
  margin-bottom: 5px;
}
</style>
