<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
<!--<AssignmentThree></AssignmentThree>-->
<!--    <ProjectFour></ProjectFour>-->
    <assignment-four></assignment-four>

  </div>
</template>

<script>
// import AssignmentTwo from "@/components/Assignments/AssignmentTwo.vue";
// import AssignmentThree from "@/components/Assignments/AssignmentThree.vue";
// import ProjectFour from "@/components/ProjectFour.vue"
import AssignmentFour from "@/components/Assignments/AssignmentFour.vue"


export default {
  name: 'App',
  components: {
    // AssignmentTwo,
    // AssignmentThree,
    // ProjectFour
    AssignmentFour
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
