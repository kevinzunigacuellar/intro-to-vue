<template>
  <div class="flex min-h-screen justify-center items-center">
    <div class="border bg-gray-200 rounded-md w-96 p-8">
      <div class="flex justify-between items-center">
        <Header title="To do list:" />
        <Button text="Add new task" />
      </div>
      <div class="mt-4">
        <Tasks
          @delete-task="deleteTask"
          @toggle-reminder="toggleReminder"
          :tasks="tasks"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Tasks from './components/Tasks.vue'
import Header from './components/Header.vue'
import Button from './components/Button.vue'
export default {
  name: 'App',
  components: {
    Header,
    Button,
    Tasks,
  },
  emits: ['delete-task', 'toggle-reminder'],
  data() {
    return {
      tasks: [],
      users: [],
    }
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id)
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map(task =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      )
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Call Michael',
        day: 'Sept 03 at 12:00pm',
        reminder: true,
      },
      {
        id: 2,
        text: 'Go to the gym',
        day: 'Sept 03 at 1:00pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'Buy groceries',
        day: 'Sept 03 at 3:00pm',
        reminder: false,
      },
    ]
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/users')
      .then(response => response.json())
      .then(json => (this.users = json))
  },
}
</script>
