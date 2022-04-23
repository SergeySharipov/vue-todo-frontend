<template>
  <div>
    <div v-bind:key="task.id" v-for="task in tasks">
      <TaskItem
        v-bind:task="task"
        v-on:update-task="$emit('update-task', task)"
        v-on:delete-task="$emit('delete-task', task.id)"
      />
    </div>
  </div>
</template>

<script>
import TaskItem from "./TaskItem.vue";

export default {
  name: "Tasks",
  components: {
    TaskItem,
  },
  props: ["tasks"],
};
</script>

<style scoped>
</style>
