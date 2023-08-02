<template>
  <section>
    <header>
      <h1>FriendList</h1>
    </header>
    <section id="app">
        <div>
          <h2>{{name}} {{friendIsFavorite===true ? '(Favorite)' : 'Not Favorite'}}</h2>
          <button @click="toggleFavorite">Toggle Favorite</button>
          <button @click="IsVisibleMethod">{{isVisible? 'Hide Details' : 'Show Details'}}</button>
          <ul v-if="isVisible">
            <li><strong>Phone:</strong>{{phoneNumber}}</li>
            <li><strong>Email:</strong> {{emailAddress}}</li>
          </ul>
        </div>
    </section>
  </section>
</template>

<script>
export default{

  // props:[
  //     'name',
  //     'phoneNumber',
  //     'emailAddress',
  //     'isFavorite',
  // ],
  props:{
    name:{
      type:String,
      required:true,
    },
    phoneNumber:{
      type:String,
      required:true,
    },
    emailAddress:{
      type:String,
      required:true,
    },
    isFavorite:{
      type:Boolean,
      required:false,
      default:false,
      validator:function(value){
       return value ===false || value === true
      }
    },
  },
  data(){
    return{
      //Return the friend data.
      //TODO in this case we are not using the friends array but we are sending different data based on the props.
      isVisible:false,
      friendIsFavorite:this.isFavorite,
    }
  },
  methods:{
  //   Display all of the methods but for 1 friend.
    IsVisibleMethod(){
      this.isVisible = !this.isVisible;
    },
    // Mutation of the prop is not good.
    toggleFavorite() {
     this.friendIsFavorite = !this.friendIsFavorite
    }
  },
}
</script>

<style>

</style>