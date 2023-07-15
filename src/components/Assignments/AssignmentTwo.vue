<template>
  <div>
    <!--    Getting the initial starting value from the counter.-->
    <header>
      <h1>Vue Events</h1>
    </header>
    <section id="assignment">
      <h2>Event Practice</h2>
      <!-- 1) Show an alert (any text of your choice) when the button is pressed -->
      <button v-on:click="showAlert()">Show Alert</button>
      <hr>
      <!-- 2) Register the user input on "keydown" and output it in the paragraph (hint: event.target.value helps) -->

<!--      Counter Btn-->
      <button v-on:click="countUP()">Count UP</button>
      <button v-on:click="countDOWN()">COUNT DOWN</button>
<!--      Starting counter.-->
      <h3 v-once>Started Counter : {{counter}}</h3>

<!--      Modified Counter-->
      <h3>{{counter}}</h3>

      <div style="margin-bottom:20px;">
        <label style="margin-bottom:20px; margin-top:20px;">Instantly rendering</label>
      </div>
      <div>
        <input type="text" v-on:input="createText">
        <p>Output : {{textOutput}}</p>
      </div>

      <hr>
      <!-- 3) Repeat 2) but only output the entered value if the ENTER key was pressed -->
      <div style="margin-bottom:20px;">
        <label>When u press enter.</label>
      </div>
      <div>
        <input type="text" v-on:keydown.enter="createText2($event, lastName)" v-on:keydown="createText">
        <!--      v-on:keydown.enter="createText2($event, this.lastName)" -->
        <p>OUTPUT : {{textOutput2}}</p>
      </div>


      <div style="margin-bottom:20px;">
        <label>When u press space.</label>
      </div>
      <div>
        <input type="text" v-on:keydown.space="createText3($event, lastName, years)">
<!--              v-on:keydown.enter="createText2($event, this.lastName)" -->
        <p>OUTPUT : {{textOutput3}}</p>
      </div>

<!--Preventing the default here when the submission occurs.-->
      <form v-on:submit.prevent>
        <div style="margin-bottom:20px;">
          <label>Enter your profession</label>
        </div>
        <div>
          <input type="text" style="border:1px solid black;padding:10px;" v-on:keydown.enter="createProfession">
          <p>Your profession is :  {{profession}}</p>
        </div>
      </form>
    </section>
  </div>
</template>
<!--TODO fix the input (clear it after submission)-->
<script>
export default{
data(){
  return{
    textOutput:'',
    textOutput2:'',
    textOutput3:'',
    lastName:'pavlovski',
    years:21,
    profession:'',
    counter:0,
  }
},
  methods:{
    showAlert(){
      alert('The Button has been pressed.!')
    },
    createText(event){
      this.textOutput= event.target.value;
    },
    createText2(event , lastName){
      this.textOutput2= event.target.value+  ' ' + lastName
    },
    createText3(event, lastName, years){
      this.textOutput3= event.target.value + ' ' + lastName +  ' ' + years
    },
    createProfession(event){
    //   We can do this. event.preventDefault() or with the modifiers
      this.profession = event.target.value;
    },
    countUP(){
      this.counter++;
    },
    countDOWN(){
      this.counter--;
    }
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

#assignment p {
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

</style>

