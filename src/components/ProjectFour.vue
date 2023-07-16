<template>
  <div>
    <header>
      <h1>Vue Dynamic styling</h1>
    </header>
    <section id="styling">
<!--      So this is the dynamic style. we are checking for the box that we passed the value in the parameter-->
<!--      This is possible with the turnary operator.  If the operator is not present we can't check for the colors. This could be for everything lets try it for text.-->
<!--      Really important that we are sending active, demo too. becuase the demo is actually the box -->
<!--      Still hard to read.-->

      <div :class="boxSelectedA ? 'secondary demo': 'demo'" @click="boxSelected('A')"></div>
      <div :class="{demo:true, active:boxSelectedB}" @click="boxSelected('B')"></div>
      <div :class="{demo:true, inactive:boxSelectedC}" @click="boxSelected('C')"></div>
    </section>
    <section id="styling">
      <div class="text" :style="{color:textSelected1 ? 'red':  'blue'}" @click="textSelected(1)">test1</div>
      <div class="text" @click="textSelected(2)">Test2</div>
      <div class="text" @click="textSelected(3)">Test3</div>
    </section>
  </div>
</template>

<script>
//get the particular item when we click on it we want to highlight it
export default{
  data(){
    return{
      //Make sure that we are selecting the correct item
        boxSelectedA:false,
        boxSelectedB:false,
        boxSelectedC:false,
        textSelected1:false,
        textSelected2:false,
        textSelected3:false,
      }
    },
  methods:{
    boxSelected(box){
      if(box==='A'){
        this.boxSelectedA=true;
      }
      else if(box==='B'){
        this.boxSelectedB=true;
      }
      else if(box==='C'){
        this.boxSelectedC=true;
      }
    },
    textSelected(text){
    if(text===1){
      this.textSelected1=true;
    }
    else if(text===2){
      this.textSelected2=true;
    }
    else if(text===3){
      this.textSelected3=true;
      }
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
.active{
  border-color:red;
  background-color:crimson;
}
.inactive{
  border-color:blue;
  background-color:steelblue;
}
.secondary{
  border-color:yellow;
  background-color:lime;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  background-color: #4fc08d;
  color: white;
  text-align: center;
}

#styling {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}

.demo {
  width: calc(100% - 32px);
  height: 100px;
  margin: 16px;
  border: 2px dashed #ccc;
}
</style>