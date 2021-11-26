<template>
    <div @dblclick="$emit('toggle-completed', task.id)" :class="[task.completed ? 'completed' : 'notcompleted', 'task']">
        <h3>
        {{ task.text }} 
        <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
</template>

<script>
export default {
    name: "Task",
    props: {
        task: Object
    },
    emits: ['delete-task', 'toggle-completed']
}
</script>

<style scoped>
.fas {
    color: red;
}
.completed {
    background-color: green;
}
.notcompleted {
    background-color: #1a1c1d;
}
</style>