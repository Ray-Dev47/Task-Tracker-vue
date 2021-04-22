<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask" />   <!-- props defined here -->
    <div v-show="showAddTask"> 
      <AddTask @add-task="AddTask" />
    </div> 
    
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" v-bind:tasks="tasks" />   <!--  we are binding it since it is an array and w'd like to make it dynamic  -->
  </div>
</template>


<script>
// here we import our created components
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from './components/AddTask'
 
// we register Header component here
export default {
  name: "App",
  components: {  
    Header,
    Tasks,
    AddTask,
  },

 // data for the task tracker and creater which will be requested
 data() {
   return {
     tasks: [], 
     showAddTask: false,
     }
   },
   methods: {
     toggleAddTask(){
       this.showAddTask = !this.showAddTask  

     }, 
     AddTask(task){
       this.tasks = [...this.tasks, task]
     },

     deleteTask(id) {
      //  console.log('task', id) to test
      if(confirm ('Are you sure?')){
      this.tasks = this.tasks.filter((task) => task.id !== id)
      }
     },
     toggleReminder(id){
          this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder}
          : task)
       }
   },

   created() { 
     this.tasks = [
       {
         id: 1,
         text: 'Doctors Apointement',
         day: 'March 1st at 2:30pm',
         reminder: true,
       },
       {
         id: 2,
         text: 'Meeting at school',
         day: 'August 3rd at 1:30pm',
         reminder: true,
       },
       {
         id: 3,
         text: 'Food Shopping',
         day: 'July 3rd at 11:30pm',
         reminder: false,
       },
     ]
    }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
} 
body {
  font-family: "Poppins", sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
