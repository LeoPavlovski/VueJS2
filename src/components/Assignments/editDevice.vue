
<!-- <li><strong>Name:</strong>{{name}}</li>
          <li><strong>Color:</strong> {{color}}</li>
          <li><strong>Phone:</strong>{{phoneNumber}}</li>
          <li><strong>Email:</strong> {{email}}</li>-->
<template>
<div>
  <form v-on:submit.prevent="editDevice">
    <div>
      <label>Name</label>
      <input type="text" v-model="nameInput">
    </div>
    <div>  <label>Color</label>
      <input type="text" v-model="colorInput"></div>
    <div>
      <label>Phone</label>
      <input type="text" v-model="phoneInput"></div>
    <div>
      <label>Email</label>
      <input type="text" v-model="emailInput"></div>
    <button>Edit Item!</button>
  </form>

</div>
</template>

<script>
export default{
  props: {
    name: {
      type: String,
      required: true,
    },
    color: {
      type: String,
      required: true,
    },
    phone: {
      type: String,
      required: true,
    },
    email: {
      type: String,
      required: true,
    },
  },
  emits:['edit-device'],
  data(){
    return {
      nameInput: this.name, // Set initial value based on the 'name' prop
      colorInput: this.color, // Set initial value based on the 'color' prop
      phoneInput: this.phone, // Set initial value based on the 'phone' prop
      emailInput: this.email, // Set initial value based on the 'email' prop
    };
  },
  methods:{
    editDevice() {
      const newItem = this.$emit('edit-device',this.nameInput, this.colorInput, this.phoneInput, this.emailInput)
     console.log(newItem);

    }
  },
}
</script>

<style>

</style>