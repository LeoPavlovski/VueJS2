<template>
  <section>
    <header>
      <h1>Device List</h1>
    </header>
    <section id="app">
      <div>
        <h2>{{name}} {{isFavorite===true ? '(Favorite)' : 'Not Favorite'}}</h2>
        <button @click="toggleFavorite">Toggle Favorite</button>
        <button @click="IsVisibleMethod">{{isVisible? 'Hide Details' : 'Show Details'}}</button>
        <button @click="deleteDevice">Delete Device</button>
        <button @click="editDevice">Edit Device</button>
        <div v-if="isEditing">
        <edit-device :name="name" :color="color" :email="email" :phone="phoneNumber"></edit-device>
        </div>
        <ul v-if="isVisible">
          <li><strong>Name:</strong>{{name}}</li>
          <li><strong>Color:</strong> {{color}}</li>
          <li><strong>Phone:</strong>{{phoneNumber}}</li>
          <li><strong>Email:</strong> {{email}}</li>

        </ul>
      </div>
    </section>
  </section>
</template>

<script>
import EditDevice from "@/components/Assignments/editDevice.vue";

export default{
  components: {EditDevice},
  emits:['toggle-favorite','toggle-delete','edit-device'],
  props:{
    id:{
      type:String,
      required:true,
    },
    name:{
      type:String,
      required:true,
    },
    color: {
      type:String,
      required:true,
    },
    email:{
      type:String,
      required:true
    },
    phoneNumber:{
      type:String,
      required:true
    },
    isFavorite:{
      type:Boolean,
      default:false,
      required:false,
    }
  },
  data(){
    return{
      isVisible:false,
      isEditing:false,
    }
  },
  methods:{
    IsVisibleMethod(){
      //isVisibleMethod.
      this.isVisible = !this.isVisible;
    },
    toggleFavorite(){
      this.$emit('toggle-favorite',this.id)
    },
    deleteDevice(){
      this.$emit('toggle-delete',this.id)
    },
    //   addCar(name,color,yearProduction){
  //   const newCar = {
  //     id: new Date().toISOString(),
  //     name: name,
  //     color: color,
  //     yearProduction: yearProduction,
  //     isFavorite:false
  //   }
  //   this.cars.push(newCar);
  // },
    editDevice() {
      this.isEditing = !this.isEditing;
      const newItem = this.$emit('edit-device',this.id);
      console.log(newItem);
    },
  },
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
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li,form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}
#app input{
  font:inherit;
  padding:0.15rem;
}
#app label{
  font-weight:bold;
  margin-right:1rem;
  width:7rem;
  display:inline-block;
}
#app form div{
  margin:1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

</style>
