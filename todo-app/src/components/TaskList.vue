<script setup>
import { ref } from 'vue';
// define props
const props = defineProps(['tasks']);
const isMarkedDone = ref('false');

const updateListStatus = (index) => {
    // get selected task's index and set the status
    if(props.tasks[index].status === 'Ongoing') {
        props.tasks[index].status = 'Completed';
    } else {
        props.tasks[index].status = 'Ongoing';
    }
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
                            <!-- TO DO:
                                set function that when doneBtn is clicked will change the text inside 
                            -->
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