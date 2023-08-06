<template>
  <form v-on:submit.prevent="submitData">
    <div>
      <label>Name</label>
      <input type="text" v-model="nameInput">
    </div>
    <div>
      <label>Color</label>
      <input type="text" v-model="colorInput">
    </div>

    <div>
      <label>Email</label>
      <input type="text" v-model="emailInput">

    </div>
    <div>
      <label>Phone</label>
      <input type="text" v-model="phoneInput">
    </div>
    <button>Add New Device!</button>

  </form>
</template>
<script>
export default{

  emits:['add-device'],

  data(){
    return{
      nameInput:'',
      colorInput:'',
      emailInput:'',
      phoneInput:'',
    }
  },
  methods:{
    //   Here we are going to submit the data.
    submitData(){
      this.$emit('add-device', this.nameInput , this.colorInput,  this.emailInput, this.phoneInput)
    }
  },
}
</script>