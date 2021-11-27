<template>
    <div class="form-container">
    <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input id="Taskinput" type="text"
       v-model="text" 
       name="text"
      placeholder="Task Name" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <DatePicker v-model="date" 
      format="dd-M-Y" 
      dark 
      :minDate="new Date()" 
      autoApply 
      :is24="false" 
      :enableTimePicker="false"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set completed</label>
      <input id="checkbox" type="checkbox" v-model="completed" name="completed" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
  </div>
</template>

<script>
import DatePicker from "vue3-date-time-picker";
import "vue3-date-time-picker/dist/main.css";

export default {
  components: {DatePicker},
    name: "AddTask",
    data() {
        return {
            text: "",
            day: "",
            completed: false
        };
    },
    methods: {
        onSubmit(e){
            e.preventDefault();
            var returndate = this.date.toString().substring(0,15)
            if (!this.text) {
                alert("Please add a task");
                return
            }
            const newTask = {
                id: Math.floor(Math.random()* 1000000),
                text: this.text,
                day: returndate,
                completed: this.completed
            }
            this.$emit("add-task", newTask);
            this.text = "";
            this.day = "";
            this.completed = false;
        }
    }
    
}
</script>

<style scoped>
.add-form{
    background-color: #1a1c1d;
    padding: 0px 20px 20px 20px;
    border-radius: 5px;
    margin: auto;
}
.form-container {
  display: flex;
  background-color: #262a2b;
  border-radius: 5px;
  width: 80%;
  margin: 10px auto 10px auto;
  padding: 10px;
  align-items: center;
  justify-content: center;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  color: #d2d7db;
  border-radius: 5px;
  height: 40px;
  margin: 5px;
  font-size: 17px;
}
.form-control-check {
  border-radius: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 1;
  justify-content: center;
  align-items: center;
  width: 20px;
  height: 20px;
}
#Taskinput{
  color: "white";
  background-color: #212121;  
}
</style>