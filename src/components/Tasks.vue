<template>
  <div>
    <div :key="task.id" v-for="task in tasks">
      <TaskItem
        :task="task"
        @update-task="$emit('update-task', task)"
        @delete-task="$emit('delete-task', task.id)"
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
