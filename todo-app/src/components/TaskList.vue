<script setup>
import { ref } from 'vue';
// define props
const props = defineProps(['tasks']);
const isMarkedDone = ref('false');

const emit = defineEmits(['updatingTaskStatus']);

const updateListStatus = (index) => {
    emit('updatingTaskStatus', index);
}
</script>

<template>
    <div>
        <table>
            <thead>
                <th>Task</th>
                <th>Status</th>
                <th>Actions</th>
            </thead>
            <tbody>
                <tr v-for="(task, index) in tasks" :key="index">
                    <td :class="(task.status === 'Completed') ? 'markedDone' : '' ">{{task.name}}</td>
                    <td :class="(task.status === 'Completed') ? 'statusDone' : '' ">{{task.status}}</td>
                    <td>
                        <div class="tableBtn">
                            <button class="doneBtn" @click="updateListStatus(index)">
                                <span v-if="(task.status === 'Completed')">Mark as Undone</span>
                                <span v-else>Mark as Done</span>
                            </button>
                            <button class="delete">Delete</button>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>