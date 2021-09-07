<template>
  <ul :key="task.id" v-for="task in tasks">
    <Task
      @delete-task="$emit('delete-task', task.id)"
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      :task="task"
    />
  </ul>
</template>

<script>
import Task from './Task.vue'
export default {
  name: 'Tasks',
  props: {
    tasks: {
      type: Array,
      default: () => [],
    },
  },
  emits: ['delete-task', 'toggle-reminder'],
  components: {
    Task,
  },
}
</script>

<style></style>
