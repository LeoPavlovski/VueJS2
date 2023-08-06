<template>
<!--  Two components for the activeUser, userdata-->
<active-user></active-user>
<user-data></user-data>
</template>

<script>
import ActiveUser from "@/components/Assignments/ActiveUser.vue";
import UserData from "@/components/Assignments/UserData.vue"
export default{
  components:{
    ActiveUser,
    UserData
  },
  data(){
    return{

    }
  }
}
</script>

<style>

</style>