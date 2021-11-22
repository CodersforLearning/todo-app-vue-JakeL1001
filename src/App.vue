<template>
  <Header title="Welcome to Your Vue.js App"/>
  <AddTask @add-task="addTask"/>
  <Tasks @toggle-reminder="toggleReminder" 
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
      tasks: []
    }
  },
  methods: {
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id){
      if (confirm("Are you sure you want to delete this task?")){
      this.tasks = this.tasks.filter(task => task.id !== id)
    }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map(task => {
        if (task.id === id){
          task.reminder = !task.reminder
        }
        return task
      })
    }
  },
  created() {
    this.tasks = [{id:1, text: "submit todo app", day: "November 17th at 11:50pm", reminder:true,}, {id:2, text: "make todo app", day: "November 12th at 11:50pm", reminder:false,}]
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
  margin-top: 60px;
}

</style>
