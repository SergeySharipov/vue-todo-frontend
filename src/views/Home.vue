<template>
  <div id="app">
    <AddTask @add-task="addTask" />
    <Tasks :tasks="tasks" @update-task="updateTask" @delete-task="deleteTask" />
  </div>
</template>

<script>
/* eslint-disable no-console */
import Tasks from "../components/Tasks";
import AddTask from "../components/AddTask";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    async addTask(newTask) {
      const { title, description, completed } = newTask;

      try {
        const res = await axios.post("http://localhost:8080/api/tasks", {
          title,
          description,
          completed,
        });
        this.tasks = res.data;
      } catch (err) {
        console.log(err);
      }
    },
    async updateTask(updatedTask) {
      const { id, title, description, completed } = updatedTask;

      try {
        const res = await axios.put(`http://localhost:8080/api/tasks/${id}`, {
          title,
          description,
          completed,
        });
        this.tasks = res.data;
      } catch (err) {
        console.log(err);
      }
    },
    async deleteTask(id) {
      try {
        const res = await axios.delete(`http://localhost:8080/api/tasks/${id}`);
        this.tasks = res.data;
      } catch (err) {
        console.log(err);
      }
    },
  },
  async created() {
    try {
      const res = await axios.get("http://localhost:8080/api/tasks");
      this.tasks = res.data;
    } catch (err) {
      console.log(err);
    }
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
