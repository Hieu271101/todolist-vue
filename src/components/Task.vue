<template>
    <div @dblclick="toggle(task.id)" :class="[task.completed? 'reminder': '','row']">
          {{task.title}}
          <i class="fa-solid fa-trash-can" @click="deleteTask(task.id)" ></i>
          <!-- <button type="button" @click="deleteTask(task.id)">X </button> -->
    </div>
 
</template>

<script>
export default {
    name:'Task',
    props:{
        task:Object
    },
    methods:{
        deleteTask(id){
            this.$emit('deleteTask', id);
        },
        toggle(id){
            this.$emit('toggle-reminder', id);
        }
    }

}
</script>
<style scoped>
    .row{
        border: 1px solid black;
        padding: 10px;
       border-radius: 5px;
      
       margin-bottom: 10px;
    }
    i{
        float: right;
        background: none;
        border: none;
        font-weight: bold;
        font-size: 25px;
        cursor: pointer;
        
    }
    .reminder{
        border-left: 20px solid green;
    }
</style>