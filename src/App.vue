<template>
  <Header @toggle-add-task="toggleAddTask"
  @clear-list="clearList"
  @clear-completed="clearCompleted"
  title="To-Do List" 
  :showAddTask="showAddTask"/>
  <div v-if="showAddTask">
    <AddTask @add-task="addTask"/>
  </div>
  <Tasks @toggle-completed="togglecompleted" 
  @delete-task="deleteTask" :tasks="tasks" />
</template>

<script>
import Header from './components/Header.vue'
import Tasks from "./components/Tasks.vue"
import AddTask from "./components/AddTask.vue"

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return{
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
    clearList(){
      if (confirm("Are you sure you want to clear all tasks?")){
      this.tasks = []
      }
    },
    clearCompleted(){
      this.tasks = this.tasks.filter(task => !task.completed)
    },
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id){
      if (confirm("Are you sure you want to delete this task?")){
      this.tasks = this.tasks.filter(task => task.id !== id)
    }
    },
    togglecompleted(id){
      this.tasks = this.tasks.map(task => {
        if (task.id === id){
          task.completed = !task.completed
        }
        return task
      })
    }
  },
  created() {
    this.tasks = [{id:1, text: "Example Task!", day: "Wed Nov 17 2021", completed:true,}, {id:2, text: "Double Click Me!", day: "Fri Nov 12 2021", completed:false,}]
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #d2d7db;
  background-color: #2d3436;
}

</style>
