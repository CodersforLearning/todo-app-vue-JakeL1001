<template>
  <header>
    <div class="Header">
      <h1>{{ title }}</h1>
      <Button @button-click="$emit('toggle-add-task')" 
      :text="showAddTask ? 'Close' : 'Add Task'" 
      :color="showAddTask ? 'red': 'green'" />
      <Button @button-click="$emit('clear-list')"
      :text="'Clear List'"
      :color="'red'" />
      <Button @button-click="$emit('clear-completed')"
      :text="'Clear Completed Tasks'"
      :color="'orange'" />
    </div>
  </header>
</template>

<script>
import Button from './Button'

export default {
  name: 'Header',
  props: {
    title: String,
    showAddTask: Boolean
  },
  components: {
    Button
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header{
  justify-content: center;
  align-items: center;
}
div.Header{
  background-color: #262a2b;
  border-radius: 5px;
  padding: 10px;
  margin: 10px auto 10px auto;
  width: 80%;
  align-items: center;
  justify-content: center;
}
h1{
  font-size: 2em;
  margin: 0;
}
</style>
