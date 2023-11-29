<script setup>
import TaskComponent from '@/components/TaskComponent.vue'
import { ref } from 'vue'

let tasks = ref([])
let currentTask = ref('')

function deleteTask(id) {
  tasks.value.splice(id, 1)
}

function createTask(task) {
  if (currentTask.value.trim() == '') {
    return
  }

  tasks.value.push(task)
  currentTask.value = ''
}
</script>

<template>
  <div class="bg-gray-50 w-96 shadow-md rounded mx-auto mt-12 px-4 py-3">
    <h1 class="text-2xl font-semibold select-none">Tareas</h1>

    <div class="flex mt-2 mb-1">
      <input
        class="rounded-r-none w-4/5 h-8 px-2 py-1 border rounded border-blue-200 focus:border-blue-600 focus:outline-none"
        v-model="currentTask"
        @keyup.enter="createTask(currentTask)"
      />
      <span
        class="rounded-l-none w-1/5 h-8 text-xl rounded bg-blue-600 text-center text-white hover:cursor-pointer select-none hover:bg-blue-700"
        @click="createTask(currentTask)"
        >+</span
      >
    </div>

    <TaskComponent
      :key="id"
      v-for="(task, id) in tasks"
      :task="task"
      :id="id"
      @deleteTask="deleteTask"
    />
  </div>
</template>
