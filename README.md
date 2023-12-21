# VUEJS Todo App
---
A simple todo application created using VueJS 

### Topics being explored:
* VueJS Composition API
> Composition API is one of VueJS API styles
* Defining Props
> Props are data registered to a component
* Reactive state using ref
> ref allows direct reference to specific DOM element
* Passing Props from Parent to Child Component
> in composition API, passing props can be accessed in a child component through defineProps({})
```
<script setup>
    const props = defineProps({
        taskLists
        /* taskLists.taskName,
         * taskLists.status
         */
    })
</script>
```
* Emit event from Child to Parent component
> in composition API, emitting event or listening to data from child to Parent can be processed through custom events or defineEmits({})

__Child component__
```
// child component
<script setup>
    const taskName = ref('');
    const status = ref('Ongoing');

    const emit = defineEmits(['addingTask']);

    const task = {
        name: taskName.value;
        status: status.value;
    }

    emit('addingTask', task);

</script>
```
__Parent component__
```
// parent component
<script setup>
    const taskLists = ref([]);
    const handleAddingTask = (task) => {
        taskLists.value.push({
            taskName: 'task.name',
            status: 'task.status'
        })
    }
</script>

<template>
    <child-component @addingTask="handleAddingTask"></child-component>
</template>

```
