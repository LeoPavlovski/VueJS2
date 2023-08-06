<template>
  <section>
    <header>
      <h1>FriendList</h1>
    </header>
    <section id="app">
        <div>
          <h2>{{name}} {{isFavorite===true ? '(Favorite)' : 'Not Favorite'}}</h2>
          <button @click="toggleFavorite">Toggle Favorite</button>
          <button @click="toggleName">Toggle Name</button>
          <button @click="IsVisibleMethod">{{isVisible? 'Hide Details' : 'Show Details'}}</button>
          <button @click="deleteFriend">Delete Friend</button>
          <ul v-if="isVisible">
            <li><strong>Phone:</strong>{{phoneNumber}}</li>
            <li><strong>Email:</strong> {{emailAddress}}</li>
          </ul>
        </div>
    </section>
  </section>
</template>

<script>

export default {

  // props:[
  //     'name',
  //     'phoneNumber',
  //     'emailAddress',
  //     'isFavorite',
  // ],
  //Just to delcare that we are using emits here, easy for the developer.
  // emits:['toggle-favorite'],
  // They are going to catch the error.
  emits: ['toggle-favorite', 'toggle-name'],


  // emits:{
  //   'toggle-favorite':function(id){
  //     if(id){
  //       return true;
  //     }
  //     else{
  //       console.warn('Id is missing!')
  //       return false
  //     }
  //   },
  // },
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
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
  data() {
    return {
      //Return the friend data.
      //TODO in this case we are not using the friends array but we are sending different data based on the props.
      isVisible: false,
    }
  },
  methods: {
    // Display all of the methods but for 1 friend.
    IsVisibleMethod() {
      this.isVisible = !this.isVisible;
    },
    // Mutation of the prop is not good.
    toggleFavorite() {
      // Yep this works. so basically when im having to change something here, while updateing the interface. Im using emit
      // Emit takes parameters, what u call the event and on what it occurs, because we are going to have multiple elements in the array.
      this.$emit('toggle-favorite', this.id)
    },
    toggleName() {
      const nameValue = this.$emit('toggle-name', this.id)
      console.log(nameValue);
    },
    deleteFriend(){

    }
  },
};
</script>

<style>

</style>