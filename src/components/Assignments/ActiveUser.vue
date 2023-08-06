<template>
  <div>
<!--    This is for the username-->
    <h3>Username: {{username}}</h3>
    <h4>Age:{{age}}</h4>
  </div>
</template>

<script>
export default{
  props:{
    username:{
      type:String,
      required:true,
    },
    age:{
      type:Number,
      required:true,
    },
  },
  data(){
    return{
      // This works, but we need to get them as props. Because we might have more components.
    }
  }
}
</script>

<style>

</style>