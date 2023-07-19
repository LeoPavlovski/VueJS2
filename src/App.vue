<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
<!--<AssignmentThree></AssignmentThree>-->
<!--    <ProjectFour></ProjectFour>-->
<!--    <assignment-four></assignment-four>-->

<!--    <assignment-five></assignment-five>-->
    <assignment-six></assignment-six>
  </div>
</template>

<script>
// import AssignmentTwo from "@/components/Assignments/AssignmentTwo.vue";
// import AssignmentThree from "@/components/Assignments/AssignmentThree.vue";
// import ProjectFour from "@/components/ProjectFour.vue"
// import AssignmentFour from "@/components/Assignments/AssignmentFour.vue"
// import AssignmentFive from "@/components/Assignments/AssignmentFive.vue"
import AssignmentSix from "@/components/Assignments/AssignmentSix.vue"

export default {
  name: 'App',
  components: {
    // AssignmentTwo,
    // AssignmentThree,
    // ProjectFour
    // AssignmentFour
    // AssignmentFive
    AssignmentSix
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
