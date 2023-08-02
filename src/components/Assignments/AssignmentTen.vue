<template>
  <div>
<!--    This is important because here we are pasing the data to the component. Each individual componnet is going to have different data.-->
    <friend-component :is-favorite="friend.isFavorite" :name="friend.name" :phone-number="friend.phone" :email-address="friend.email"
      @toggle-favorite="toggleFavoriteStatus" @toggle-name="toggleNameStatus" :id="friend.id" v-for="friend in friends" v-bind:key="friend.id"></friend-component>

    <new-friend @add-contact="addContact"></new-friend>

    <!--    Added additional component.-->
  </div>

</template>

<script>
import friendComponent from "@/components/friendComponent.vue";
import newFriend from "@/components/newFriend.vue";
export default{
  data(){
    return{
      friends:[
        {
          'id':'Antonio',
          'name':'Antonio Lorenz',
          'phone':'01234 5678 991',
          'email':'antonio@localhost.com',
          'isFavorite':true,
        },
        {
          'id':'Manuel',
          'name':'Manuel Lorenz',
          'phone':'01234 5678 991',
          'email':'manuel@localhost.com',
          'isFavorite':false,

        },
      ],
      closeFriends:[
        {
          id:'CloseFriend1',
        //   To be continued.
        }
      ]
    }
  },

  components:{
    friendComponent,
    newFriend
  },
  methods:{
    toggleFavoriteStatus(friendId){
     const identifiedFriend = this.friends.find(friend =>friend.id === friendId);
      // This is going to change the data.
      identifiedFriend.isFavorite = !identifiedFriend.isFavorite
    },
    toggleNameStatus(friendId){
      const changedName = this.friends.find(friend=>friend.id === friendId);
      changedName.newName = !changedName.newName
    },
    addContact(name,phone,email){
      const newFriend = {
        id:new Date().toISOString(),
        name:name,
        phone:phone,
        email:email,
        isFavorite:false,
      }
      this.friends.push(newFriend)
    }
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


