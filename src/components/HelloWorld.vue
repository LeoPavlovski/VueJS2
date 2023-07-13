<template>
<section>
  <h2>Your name {{this.name}}</h2>
<p v-for="name in names" :key="name">
    {{name}}
</p>
<p>Your age {{this.age}}</p>
<p>Your Age in 5 years {{this.age+5}}</p>
<p>Favorite Number : {{this.findFavoriteNumber()}} With a function</p>
<p>Favorite Number  : {{this.randomNumber}} With a data object.</p>
<!--  Rendering the image with the v-bind-->
<div>
  <img><a v-bind:href="this.randomImage">Random Image</a>
</div>
<input type="text" v-model="userInput">
  <btn @click="AddName()">Add Name</btn>
</section>
</template>

<script>
  export default {
  data() {
    return {
      age: 21,
      name: "Leo",
      LowNumber: "You got a low number!",
      highNumber: "You got a high number",
      randomImage: "https://upload.wikimedia.org/wikipedia/commons/thumb/9/95/Vue.js_Logo_2.svg/1200px-Vue.js_Logo_2.svg.png",
      randomNumber: Math.random(),
      userInput: "",
      inputName:'',
      names:[],
    };
  },
  methods: {
    findFavoriteNumber() {
      const number = Math.random();
      console.log(number);
      if (number < 0.5) {
        return this.LowNumber;
      }
      return this.highNumber;
    },
    AddName(){
      let addingName = this.names.push(this.userInput);
      this.userInput="";
      return addingName;
    },
  },
};
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

section {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}

h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #970076;
  margin: 0 0 1rem 0;
}

p {
  font-size: 1.25rem;
  font-weight: bold;
  background-color: #970076;
  padding: 0.5rem;
  color: white;
  border-radius: 25px;
}

input {
  font: inherit;
  border: 1px solid #ccc;
}

input:focus {
  outline: none;
  border-color: #1b995e;
  background-color: #d7fdeb;
}

button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

button:hover,
button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>

