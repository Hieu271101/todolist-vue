<template>
  <form>
    <h1>Todo List</h1>
     <div class="loading" v-if="loading">
        <img src="https://upload.wikimedia.org/wikipedia/commons/c/c7/Loading_2.gif?20170503175831" alt="">
     </div>
    <div class="wrap" v-else >
      <Tasks
        @toggle-reminder="toggleChecked"
        @deleteTask="taskDeleted"
        :tasks="tasks"
      ></Tasks>
      <Button v-show="!showAddTask" @showTask="showTask"></Button>
      <div v-show="showAddTask">
        <AddTask @closeAdding="closeAdding" @add-Task="addTask"></AddTask>
      </div>
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
  data() {
    return {
      tasks: [],
      showAddTask: false,
      loading: true,
    }
  },

  async created() {
    // this.tasks=[
    //   {
    //   userID:'1',
    //   id:'1',
    //   title:'delectus aut authem',
    //   completed:false,
    //   },
    //     {
    //   userID:'1',
    //   id:'2',
    //   title:'delectus aut authem',
    //   completed:true,
    //   },
    //     {
    //   userID:'1',
    //   id:'3',
    //   title:'delectus aut authem',
    //   completed:true,
    //   }
    // ]
    // this.tasks = await this.fetchTask()
      
    this.tasks= await fetch('https://jsonplaceholder.typicode.com/todos?_start=0&_limit=5&_delay=3000')
  .then(response => response.json());
  // .then(data => console.log(data));
  
 
  this.loading=false
  },
  methods: {
    taskDeleted(id) {
      if (confirm('are u want to delete')) {
        this.tasks = this.tasks.filter((task) => task.id != id)
      }
    },
    toggleChecked(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, completed: !task.completed } : task,
      )
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    showTask() {
      this.showAddTask = !this.showAddTask
    },
    closeAdding() {
      this.showAddTask = !this.showAddTask
    },
    // async fetchTask() {
    //   const res = await fetch(
    //     'https://jsonplaceholder.typicode.com/todos?_start=0&_limit=5&_delay=3000',
    //   )
    //   const data = res.json()
    //   this.loading=false
    //   return data

    // },
  },

  components: {
    Tasks,
    AddTask,
    Button,
  },
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

form {
  border: 1px solid black;
  padding: 20px;
  width: 50%;
  height: 50%;
  margin: auto;
  border-radius: 15px;
}
</style>
