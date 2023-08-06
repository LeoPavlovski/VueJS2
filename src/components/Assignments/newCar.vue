<template>
  <form v-on:submit.prevent="submitData">
    <div>
      <label>Name</label>
      <input type="text" v-model="nameInput">
    </div>
    <div>
      <label>Year of production</label>
      <input type="text" v-model="yearProductionInput">
    </div>

    <div>
      <label>Color</label>
      <input type="text" v-model="colorInput">

    </div>

    <button>Add New Car!</button>

  </form>
</template>

<script>
export default{

  emits:['add-car','delete-car'],

  data(){
    return{
      yearProductionInput: '',
      nameInput:'',
      colorInput:'',
    }
  },
  methods:{
  //   Here we are going to submit the data.
    submitData(){
      const submitObj = this.$emit('add-car', this.nameInput, this.colorInput, this.yearProductionInput)
      console.log(submitObj)
    },
  },
}
</script>

<style>

</style>