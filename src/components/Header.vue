<template>
  <header>
        <h1>{{ title }}</h1>  <!--title props consumed here -->
   <Button @btn-click="$emit('toggle-add-task')"  :text="showAddTask ? 'Close' : 'Add'" :color="showAddTask  ? 'red' : 'green'" />  <!--button props creation -->
  </header>
</template>


<script>
// import the button component here'      
import Button from './Button'

export default {
    name: 'Header',
    props: {   //props consumed here
         title: String,  
         showAddTask: Boolean,         
  },
  // we register button component here
  components: {
      Button,
      }
  }

</script>



<style scoped>
   header {
       display: flex;
       justify-content: space-between;
       align-items: center;
       margin-bottom: 20px;
}
</style>