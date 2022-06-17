<template>
    <div>
        <i   class="fa-solid fa-plus fa-2xl"  @click="onClick()"></i>
        <!-- <button type="button" @click="onClick()">+</button> -->
    </div>
</template>

<script>
export default {
    name:'Button',
    data(){
            return {
                show:true
            }
    },
    methods:{
        onClick(){
            this.$emit('showTask')
           
        }
    }
}
</script>

<style  scoped>
    i{
        cursor: pointer;
    }
</style>