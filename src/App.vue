<template>
  <div class="container">
    <Header title="Task Tracker" />
    <AddTask v-on:add-task="addTask" />
    <Tasks
      v-on:toggle-reminder="toggleReminder"
      v-on:delete-task="deleteTask"
      v-bind:tasks="tasks"
    />
  </div>
</template>

<script>
import Tasks from "./components/Tasks";
import Header from "./components/Header";
import AddTask from "./components/AddTask";

export default {
  name: "App",
  components: { Header, Tasks, AddTask },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter(item => item.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map(task =>
        task.id == id ? { ...task, reminder: !task.reminder } : task
      );
    }
  },
  data() {
    return { tasks: [] };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Pick up groceries",
        day: "October 4, 2021 at 3:00pm",
        reminder: true
      },
      {
        id: 2,
        text: "Meeting with Business",
        day: "October 5, 2021 at 1:00pm",
        reminder: true
      },
      {
        id: 3,
        text: "Call Doctor",
        day: "October 6, 2021 at 9:00am",
        reminder: true
      },
      {
        id: 4,
        text: "Change car oil",
        day: "October 9, 2021 at 8:00am",
        reminder: false
      }
    ];
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
