<script setup>
import { ref } from 'vue';

const newTask = ref('');

const emit = defineEmits(['addingTask']);

const onSubmit = () => {
    if(!newTask.value){
        alert('Please add a task in the field!');
        return;
    }

    const addedTask = newTask.value;
    // pass the value of the input field to the parent component

    emit('addingTask', addedTask);
    newTask.value = ''
}
</script>

<template>
    <div>
        <h1>A Todo App</h1>
        <form @submit.prevent="onSubmit">
            <div class="content-container">
                <input type="text" v-model="newTask" placeholder="Enter the task"/>
                <button class="addTaskBtn">Add Task</button>
            </div>
            
        </form>
    </div>
</template>