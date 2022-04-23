<template>
  <div class="task-item" v-bind:class="{ 'is-complete': task.completed }">
    <input
      type="checkbox"
      v-on:change="markComplete"
      v-bind:checked="task.completed"
    />
    <div>
      <h4>{{ task.title }}</h4>
      <p>{{ task.description }}</p>
    </div>
    <button @click="$emit('delete-task', task.id)" class="btn-delete">x</button>
  </div>
</template>

<script>
export default {
  name: "TaskItem",
  props: ["task"],
  methods: {
    markComplete() {
      this.task.completed = !this.task.completed;
     // const { id, title, description, completed } = this.task;
      this.$emit("update-task");
    },
  },
};
</script>

<style scoped>
.task-item {
  align-self: center;
  margin: auto;
  width: 500px;
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
  display: flex;
  align-items: center;
  text-align: center;
  justify-content: space-between;
}

.is-complete {
  text-decoration: line-through;
}

.btn-delete {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>

