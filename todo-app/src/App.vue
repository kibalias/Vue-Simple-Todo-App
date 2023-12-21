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

const handleUpdatingTask = (index) => {
    // get selected task's index and set the status
    if(tasks.value[index].status === 'Ongoing') {
        tasks.value[index].status = 'Completed';
    } else {
        tasks.value[index].status = 'Ongoing';
    }
  }

</script>

<template>
  <main>
    <div class="container">
      <AddTask @addingTask="handleAddingTask"/>
      <TaskList :tasks=tasks @updatingTaskStatus="handleUpdatingTask" />
    </div>
  </main>
</template>
