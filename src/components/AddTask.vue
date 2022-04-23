<template>
  <div>
    <form @submit.prevent.stop="addTask">
      <input
        type="text"
        v-model="title"
        name="title"
        placeholder="Add Task Title..."
      />
      <input
        type="text"
        v-model="description"
        name="description"
        placeholder="Add Task Description..."
      />
      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      title: "",
      description: ""
    };
  },
  methods: {
    addTask() {
      const newTask = {
        title: this.title,
        description: this.description,
        completed: false,
      };
      this.$emit("add-task", newTask);

      this.title = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}

input[type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}
</style>


