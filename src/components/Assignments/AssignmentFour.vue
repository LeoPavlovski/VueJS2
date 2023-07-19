<template>
  <div>
    <header>
      <h1>Vue Styling</h1>
    </header>

    <section id="assignment">
      <!-- 1) Fetch the user input and use it as a CSS class -->
      <!-- The entered class should be added to the below paragraph -->
<!--      Witht he v-model i can get the userInput. really fast.-->
      <input  type="text" v-on:keyup.enter="userInput" v-model="userInput">
      <!-- (available classes: "user1", "user2") -->
<!--Toggle this paragraph-->
      <p :class="paraClasses">
        Style me!
      </p>

      <button @click="paragraphVisibility()">Toggle Paragraph</button>
      <!-- 2) Use the "visible" and "hidden" classes to show/ hide the above paragraph -->
      <!-- Clicking the button should toggle between the two options -->

      <!-- 3) Add dynamic inline styling to the below paragraph and let the user enter a background-color -->
<!--      This is how we are getting the input, and actually makin sure that the we have clear explanation of what we are doing .-->
      <input type="text" v-model="color">
      <p :style="{color : color}">Style me inline!</p>
    </section>
  </div>
</template>

<script>
export default{
  data(){
    return {
      //return the data.
      userInput:'',
      paragraphVisible:true,
      inputbackgroundColor:'',
      color:'',
    }
  },
  methods:{
  paragraphVisibility(){
    this.paragraphVisible = !this.paragraphVisible;
  },
  },
  computed:{
    paraClasses(){
      return{
        user1:this.userInput==='user1',
        user2:this.userInput==='user2',
        visible:this.paragraphVisible,
        hidden:!this.paragraphVisible,
      }
    },
  }
}
</script>

<style>
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
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  background-color: #1b995e;
  color: white;
  text-align: center;
}

#assignment {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}

#assignment h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #1b995e;
  margin: 0 0 1rem 0;
}

p {
  font-size: 1.25rem;
  font-weight: bold;
  background-color: #8ddba4;
  padding: 0.5rem;
  color: #1f1f1f;
  border-radius: 25px;
}

#assignment input {
  font: inherit;
  border: 1px solid #ccc;
}

#assignment input:focus {
  outline: none;
  border-color: #1b995e;
  background-color: #d7fdeb;
}

#assignment button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#assignment button:hover,
#assignment button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

.user1 {
  background-color: blue;
  color: white;
}

.user2 {
  background-color: purple;
  color: white;
}

.hidden {
  display: none;
}

.visible {
  display: block;
}

</style>