<template>
  <button class="px-4 py-2 rounded-lg bg-gray-400 hover:bg-gray-500">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    text: {
      type: String,
      default: 'click here',
    },
    color: String,
  },
}
</script>
