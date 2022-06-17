<template>
    <div>
        <button type="button" @click="onClick" >
            Cancel 
        </button>
    </div>
</template>

<script>
export default {
    name: 'Cancel',

    methods: {
        onClick(){
            this.$emit('closeAdding')
        }
    },
};
</script>

<style scoped>
    button{
        width: 100px;
        height: 30px;
    }
</style>