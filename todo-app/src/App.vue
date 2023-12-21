<script setup>
import AddTask from './components/AddTask.vue'
import TaskList from './components/TaskList.vue'
import { ref } from 'vue';

const tasks = ref([]);
tasks.value = [
  {
  name: 'Create a simple todo app with Vue',
  status: 'Ongoing'
  },
  {
    name: 'Learn Laravel',
    status: 'Ongoing'
  },
  {
    name: 'Learn REST API',
    status: 'Ongoing'
  },
]

const handleAddingTask = (addedTask) => {
  tasks.value.push({
    name: addedTask,
    status: 'Ongoing'
  })
}

</script>

<template>
  <main>
    <div class="container">
      <AddTask @addingTask="handleAddingTask"/>
      <TaskList :tasks=tasks />
    </div>
  </main>
</template>
