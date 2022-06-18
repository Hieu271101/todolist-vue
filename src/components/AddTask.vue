<template>
  

  <form v-show="checked" @submit="onSubmit">
    <label for=""><h2>Title</h2></label>
        <input type="text" v-model="title" class="input">
        <div class="button">
           <input type="submit" value="Save Task" class="submitBut">
           <Cancel  @closeAdding='closeAdding'></Cancel>
        <!-- <button type="button">Cancel</button> -->
        </div>
  </form>
 
  <div class="butt">
       
  </div>
</template>

<script>
import Cancel from './Cancel.vue'
export default {
  name: 'AddTask',
  data() {
    return {
      title: '',
      checked:true
    }
  },
  components:{
    Cancel
  },

  methods: {
    onSubmit(e) {
      e.preventDefault()
      if (!this.title) {
        alert('please add a task')
        return
      }
      const newTask = {
        userID: 1,
        id: Math.floor(Math.random() * 1000),
        title: this.title,
        completed: this.completed,
      }
      console.log(newTask)
      this.$emit('add-Task', newTask);
        (this.userID = ''),
        (this.id = ''),
        (this.title = ''),
        (this.completed = '')
    },
    closeAdding(){
     this.$emit('closeAdding')
    }
  },
}
</script>

<style scoped>
  .button{
    display: flex;
    justify-content: space-around;
    margin: 10px;
  }
  .submitBut{
    width: 100px;
    height: 30px;
  }
  form{
    border: none;
  }
  form .input{
    width: 300px;
    padding: 15px;
  }
</style>
