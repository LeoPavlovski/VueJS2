<template>
  <section>
    <header>
      <h1>FriendList</h1>
    </header>
    <section id="app">
        <div>
          <h2>{{name}} {{friendIsFavorite==="1" ? '(Favorite)' : 'Not Favorite'}}</h2>
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

  props:[
      'name',
      'phoneNumber',
      'emailAddress',
      'isFavorite',
  ],
  data(){
    return{
      //Return the friend data.
      //TODO in this case we are not using the friends array but we are sending different data based on the props.
      friend:
         {
          'id':'Manuel',
          'name':'Manuel Lorenz',
          'phone':'01234 5678 991',
          'email':'manuel@localhost.com'
         },

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
      if(this.friendIsFavorite === "1"){
        this.friendIsFavorite = "0"
      }
      else if(this.friendIsFavorite === "0"){
        this.friendIsFavorite = "1"
      }
    }
  },
}
</script>

<style>

</style>