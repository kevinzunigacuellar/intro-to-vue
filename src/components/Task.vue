<template>
  <li
    :class="[
      task.reminder && 'border-l-4 border-gray-600',
      'flex justify-between py-2 px-4 m-1 bg-gray-300',
    ]"
    @dblclick="$emit('toggle-reminder', task.id)"
  >
    <div>
      <p>{{ task.text }}</p>
      <p>{{ task.day }}</p>
    </div>
    <Button text="delete" @click="$emit('delete-task', task.id)" />
  </li>
</template>

<script>
import Button from './Button.vue'
export default {
  name: 'Task',
  props: {
    task: {
      type: Object,
      default: () => {},
    },
  },
  components: {
    Button,
  },
}
</script>
