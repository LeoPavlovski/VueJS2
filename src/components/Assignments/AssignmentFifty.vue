<template>
  <div>
    <DevicesComponent
        v-for="device in devices"
        :key="device.id"
        :id="device.id"
        :name="device.name"
        :color="device.color"
        :email="device.email"
        :phone-number="device.phone"
        :is-favorite="device.isFavorite"
        @toggle-favorite="toggleFavorite"
        @toggle-delete="deleteDevice"
    ></DevicesComponent>
    <new-device @add-device="addDevice"></new-device>
  </div>
</template>

<script>
import DevicesComponent from "@/components/Assignments/DevicesComponent.vue";
import NewDevice from "@/components/Assignments/newDevice.vue";
export default{
  components:{
    DevicesComponent,
    NewDevice
  },
  data(){
    return{
      devices:[
        {
          'id':'Cholesterol',
          'name':'Cholesterol Meter',
          'color':'Red',
          'email':'test123@gmail.com',
          'phone':'1-0231223',
          'isFavorite':false,
        },
        {
          'id': 'BloodPressure',
          'name': 'BloodPressure meter',
          'color': 'Black',
          'email':'test123@gmail.com',
          'phone':'1239u213',
          'isFavorite':true,
        }
      ]
    }
  },
  methods:{
    addDevice(name,color,email,phone){
      const newDevice = {
        id:new Date().toISOString(),
        name:name,
        color:color,
        email:email,
        phone:phone,
        isFavorite:false,
      }
      this.devices.push(newDevice)
    },
    // We have to find it because of the v-for loop.

    toggleFavorite(deviceId){
     const device = this.devices.find(device => device.id === deviceId);
     device.isFavorite  = !device.isFavorite;
    },
    deleteDevice(deviceId){
    this.devices = this.devices.filter(device => device.id !== deviceId)
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
