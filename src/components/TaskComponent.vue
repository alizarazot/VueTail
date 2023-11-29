<script setup>
const props = defineProps({
  task: {
    type: String,
    default: 'Fatal Error!'
  },

  id: {
    type: Number
  }
})

const emit = defineEmits(['deleteTask'])

function deleteTask(id) {
  emit('deleteTask', id)
}
</script>
<template>
  <div>
    <div class="flex justify-between bg-gray-200 rounded px-4 py-1 mt-1">
      <div>{{ props.task }}</div>
      <span
        class="rounded select-none bg-red-600 text-center text-white px-2 hover:cursor-pointer hover:bg-red-700"
        @click="deleteTask(props.id)"
        >X</span
      >
    </div>
  </div>
</template>
