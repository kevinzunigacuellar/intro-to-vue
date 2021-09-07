<template>
  <div class="text-2xl font-bold">{{ title }}</div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    title: {
      type: String,
      default: 'No title',
    },
  },
}
</script>
