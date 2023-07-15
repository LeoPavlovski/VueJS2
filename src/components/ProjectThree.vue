<template>
  <div>
<!--    Getting the initial starting value from the counter.-->
    <header>
      <h1>Vue Events</h1>
    </header>
    <section id="events">
      <h2>Events in Action</h2>
      <button @click="addBtn()">Add</button>
      <button @click="updateName()">Update Name!</button>
      <button @click.right="removeBtn()">Remove</button>
      <input type="text" v-on:input="setName($event, 'pavlovski')" v-on:keyup.enter="setNewName">
<!--      <input type="text" v-on:input="addYears">-->
      <p v-once >Starting Counter : {{counter}}</p>
      <p>Result:{{counter}}</p>
<!--      <p v-for="name in nameInputs" :key="name">Your name is :{{ name }}</p>-->
      <p >Your name is :{{confirmedName}}</p>
      <p>Your name is : {{name}}</p>
<!--      <p>Your years :{{years}}</p>-->
      <form v-on:submit.prevent="onSubmit">
        <input type="text">
        <button>Sign up</button>
      </form>
    </section>
  </div>
</template>
<!--TODO fix the input (clear it after submission)-->
<script>
export default{
  data(){
    return{
      counter:0,
      add:0,
      remove:0,
      name:'',
      nameInputs:[],
      years:'',
      confirmedName : '',
    }
  },
  methods:{
    addBtn(){
      this.counter = this.counter+1;
    },
    removeBtn(){
    this.counter = this.counter-1;
    },
    updateName() {
        this.nameInputs.push(this.name);
        // i can clear the input like that too.
        this.name = '';

    },
    setName(event , lastName){
      this.name = event.target.value + ' ' + lastName
    },
    setNewName(){
      this.confirmedName = this.name;
    },
    onSubmit(){
      alert('Submitted!')
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
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #4fc08d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#events {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#events h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #4fc08d;
  margin: 0 0 1rem 0;
}

#events p {
  font-size: 1.25rem;
  font-weight: bold;
  border: 1px solid #4fc08d;
  background-color: #4fc08d;
  color: white;
  padding: 0.5rem;
  border-radius: 25px;
}

#events input {
  font: inherit;
  border: 1px solid #ccc;
}

#events input:focus {
  outline: none;
  border-color: #1b995e;
  background-color: #d7fdeb;
}

#events button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  border-radius: 20px;
  margin: 0 1rem;
}

#events button:hover,
#events button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>

