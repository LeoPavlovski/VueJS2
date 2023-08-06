<template>
  <div>
    <form v-on:submit.prevent="saveData">
      <div>
        <label>Username</label>
        <input type="text" v-model="usernameInput">
      </div>
      <div>
        <label>Age</label>
        <input type="text" v-model="ageInput">
      </div>
      <button>Set User Data</button>
    </form>
  </div>

</template>

<script>
export default {
  emits:['save-data'],
  data(){
    return{
    //   Return the models for the inputs?
      usernameInput:'',
      ageInput:'',
    }
  },
  methods:{
    saveData(){
      this.$emit('save-data',this.usernameInput, this.ageInput)
    },

  },
}
</script>

<style>

</style>