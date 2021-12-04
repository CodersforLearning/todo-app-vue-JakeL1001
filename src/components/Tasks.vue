<template>
    <div class="task-container">
        <div class="task-list" v-if="tasks.length">
            Double click tasks to mark them as completed!
            <div class="task" :key="task.id" v-for="task in tasks">
                <Task @toggle-completed="$emit('toggle-completed',task.id)" @delete-task="$emit('delete-task', task.id)" :task="task" />
    </div>
    </div>
    </div>
</template>

<script>
import Task from './Task'

export default {
    name: "Tasks",
    props: {
        tasks: Array
    },
    components: {
        Task
    },
    emits: ['delete-task']
}
</script>

<style scoped>
.task-container {
    display: flex;
    width: 80%;
    background-color: #262a2b;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 10px auto 10px auto;
    border-radius: 5px;
    padding: 10px;
}
.task-container:empty{
    display: none;
}
.task {
    border-radius: 5px;
    padding: 10px;
    width: 100%;
    justify-content: center;
    align-items: center;
}
.task-list {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 50%;
}
</style>