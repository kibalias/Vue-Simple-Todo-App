<script setup>
// define props
const props = defineProps(['tasks'])

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
                    <td>{{task.name}}</td>
                    <td>{{task.status}}</td>
                    <td>
                        <div class="tableBtn">
                            <button class="doneBtn">Mark as Done</button>
                            <button class="delete">Delete</button>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>