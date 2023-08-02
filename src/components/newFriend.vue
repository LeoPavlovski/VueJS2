
<template>
<form v-on:submit.prevent="submitData">
  <div>
    <label>Name</label>
    <input type="text" v-model="nameInput">
</div>
  <div>
    <label>Phone</label>
    <input type="text" v-model="phoneInput">
  </div>

<div>
    <label>Email</label>
    <input type="email" v-model="emailInput">

  </div>

  <button>Add New Friend!</button>

</form>
</template>

<script>

export default{
emits:['add-contact'],

  data(){
    return{
      nameInput:'',
      phoneInput:'',
      emailInput:'',
    }
  },
  methods:{
    // onSubmit(){
    //   alert('Form has been submited')
    //   this.$emit('add-user')
    // }

    submitData(){
      this.$emit('add-contact', this.nameInput, this.phoneInput, this.emailInput)
    }
  },
}
</script>

<style>

</style>