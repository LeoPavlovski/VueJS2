<template>
  <div>
    <header>
      <h1>Vue Course Goals</h1>
    </header>
    <input type="text" id="input-goal" v-model="userInput">
    <btn v-on:click="AddGoal">Add Item</btn>
    <section id="user-goal">
      <h2>My course goal</h2>
      <!--      This is the way of how we are actually working with the api-->
      <p v-for="goals in myCourseGoals" :key="goals">
        {{goals}}
      </p>
      <p v-for="goal in goals" :key="goal">
        {{goal}}
      </p>
      <!--      This is called VUE interpolation-->
      <!--      The mustaches :D -->
      <p>{{testGoal}}</p>
<!--      Calculate the Goal-->
      <p v-html="OutputGoal()"></p>
      <!--      This v-bind most of the time we are going to use if we want to link something.-->
      <p>Testing the link<a v-bind:href="GoogleLink">Google.com</a></p>

    </section>
  </div>
</template>

<script>
export default{
  data(){
    return {
      goals:[],
      userInput:[],
      myCourseGoals:['Finish Course','Get money.'],
      myGoalA:'<h2>This is some text</h2>',
      myGoalB:'Build The vitalhealthapp',
      testGoal:'leo123',
      GoogleLink:'https://www.facebook.com',
    }
  },
  methods:{
    AddGoal(){
    let addingGoals = this.goals.push(this.userInput);
      this.userInput="";
    return addingGoals;
      },
    OutputGoal(){
     const randomGoal = Math.random();
     if(randomGoal<0.5){
       return this.myGoalA
     }
     else{
       return this.myGoalB
     }
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #4fc08d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#user-goal {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#user-goal h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #4fc08d;
  margin: 0 0 1rem 0;
}

#user-goal p {
  font-size: 1.25rem;
  font-weight: bold;
  border: 1px solid #4fc08d;
  background-color: #4fc08d;
  color: white;
  padding: 0.5rem;
  border-radius: 25px;
}

#user-goal input {
  font: inherit;
  border: 1px solid #ccc;
}

#user-goal input:focus {
  outline: none;
  border-color: #1b995e;
  background-color: #d7fdeb;
}

#user-goal button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#user-goal button:hover,
#user-goal button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

</style>
