<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
<!--    <ProjectTwo></ProjectTwo>-->
    <ProjectThree></ProjectThree>
  </div>
</template>

<script>
// import ProjectTwo from './components/ProjectTwo.vue'
import ProjectThree from './components/ProjectThree.vue'

export default {
  name: 'App',
  components: {
    // ProjectTwo,
    ProjectThree
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
