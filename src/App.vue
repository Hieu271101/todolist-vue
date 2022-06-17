<template>
  <form >
    <h1>Todo List</h1>
    <Tasks @toggle-reminder="toggleChecked" @deleteTask='taskDeleted' :tasks="tasks"></Tasks>
    <Button v-show="!showAddTask" @showTask='showTask'></Button>
    <div v-show="showAddTask">
        <AddTask @closeAdding='closeAdding' @add-Task='addTask'></AddTask>
    </div>
   
  </form>
  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Tasks from './components/Tasks.vue'
import Button from './components/Button.vue'
import AddTask from './components/AddTask.vue'
export default {
  name: 'App',
  data(){
    return {
      tasks:[],
      showAddTask: false,
     
    }
  },
  
  created(){
    this.tasks=[
      {
      userID:'1',
      id:'1',
      title:'delectus aut authem',
      completed:false,
      },
        {
      userID:'2',
      id:'2',
      title:'delectus aut authem',
      completed:true,
      },
        {
      userID:'3',
      id:'3',
      title:'delectus aut authem',
      completed:true,
      }
    ]
  },
  methods:{
    taskDeleted(id){
      if(confirm('are u want to delete')){ this.tasks=this.tasks.filter((task)=>task.id!=id)}
     
    },
    toggleChecked(id){
     this.tasks= this.tasks.map((task)=>task.id===id?{...task, completed:!task.completed}:task)
     
    },
    addTask(task){
      this.tasks=[...this.tasks, task]
    },
    showTask(){
      this.showAddTask=!this.showAddTask
    },
    closeAdding(){
      this.showAddTask=!this.showAddTask
    }
  },
 
  components: {
    Tasks,
    AddTask,
    Button
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

form{
  border: 1px solid black;
  padding: 20px;
  width: 50%;
  height: 50%;
  margin: auto;
  border-radius: 15px ;
}
</style>
