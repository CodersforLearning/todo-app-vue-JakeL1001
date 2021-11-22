<template>
  <Header @toggle-add-task="toggleAddTask" 
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
    this.tasks = [{id:1, text: "submit todo app", day: "November 17th at 11:50pm", completed:true,}, {id:2, text: "make todo app", day: "November 12th at 11:50pm", completed:false,}]
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
