<template>
  <section>
    <header>
      <h1>Car List</h1>
    </header>
    <section id="app">
        <div>
        <h2>{{name}} {{isFavorite===true ? '(Favorite)' : 'Not Favorite'}}</h2>
        <button @click="toggleFavorite">Toggle Favorite</button>
        <button @click="isVisibleMethod">{{isVisible? 'Hide Details' : 'Show Details'}}</button>
        <ul v-if="isVisible">
          <li><strong>Year of Production</strong>{{yearProduction}}</li>
          <li><strong>Color</strong> {{color}}</li>
        </ul>
          <button @click="$emit('delete-car',id)">Delete</button>
      </div>
    </section>
  </section>
</template>

<script>
export default {
  emits:['add-favorite','delete-car'],
  props:{
    id:{
      type:String,
      required:true
    },
    name:{
      type:String,
      required:true,
    },
    yearProduction:{
      type:String,
      required:true,
    },
    color:{
      type:String,
      required:true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
      validator: function (value) {
        return value === false || value === true
      }
    },
  },
  data(){
    return{
      isVisible:false,
    }
  },
  methods:{
    // toggleFavorite() {
    //   this.isFavorite = !this.isFavorite;
    // },
    isVisibleMethod(){
      this.isVisible = !this.isVisible;
    },
    toggleFavorite() {
     this.$emit('add-favorite',this.id)
      console.log('test',this.isFavorite)
    },
  }
}
</script>

<style>

</style>