<template>
  <div>
    <header>
      <h1>Monster Slayer</h1>
    </header>
<!--If the player has surrender display no controls.-->
  <div id="game">
    <section id="monster" class="container">
      <h2>Monster Health</h2>
      <div class="healthbar">
        <div class="healthbar__value" :style="monsterBarStyles"></div>
      </div>
    </section>
    <section id="player" class="container">
      <h2>Your Health</h2>
      <div class="healthbar">
        <div class="healthbar__value" :style="playerBarStyles"></div>
      </div>
    </section>
<!--    GameOver Screen is going to be here.-->
    <section class="container" v-if="winner">
      <h1>Game Ending Screen</h1>
      <h3 v-if="winner==='draw'">Draw!</h3>
<!--      display the button>-->
      <h3 v-if="winner==='monster'">Monster Won!</h3>
      <h3 v-if="winner==='player'">Player Won!</h3>
      <button @click="newGame()">Start Again!</button>
    </section>


    <section id="controls" v-if="!playerSurrenders && !gameOver">
      <button @click="playerAttack()">ATTACK</button>
      <button v-on:click="playerSpecialAttack()">SPECIAL ATTACK</button>
      <button @click="playerHealing1()">HEAL</button>
      <button @click="playerSurrender()">SURRENDER</button>
    </section>
    <section id="log" class="container">
      <h2>Battle Log</h2>
      <div v-for="(log,index) in battleLogs" v-bind:key="index">
      <ul>
      <li v-if="log.type==='attack'">Player Attacked For : {{log.value}} Points</li>
        <li v-if="log.type==='monsterAttacking'">Monster Attacked For : {{log.value}} Points</li>
        <li v-if="log.type==='specialAttack'">Special Attack For : {{log.value}} HitPoints</li>
        <li v-if="log.type==='monsterHealing'">Monster Healed For : {{log.value}} Points</li>
        <li v-if="log.type==='playerHealing'">Player Healed For : {{log.value}} Points</li>
      </ul>
      </div>
      <ul>
        <li v-if="playerSurrenders">Player Has Surrendered!</li>
      </ul>

    </section>
    </div>
  </div>

</template>

<script>
export default {
  data(){
    return{
      playerAttacks:[],
      playerHealth:100,
      monsterHealth:100,
      battleLogs:[],
      playerHealing:[],
      monsterHeals:[],
      playerSurrenders:false,
      gameOver:false,
      winner:null,
    }
  },
  methods:{
    playerAttack(){
      //Random Values
      let attack = Math.floor(Math.random() * (10-5) +5);
      console.log("Player Attacked!", attack)
      this.monsterHealth= this.monsterHealth- attack;
      this.battleLogs.push({type:'attack', value:attack})
      this.monsterAttack();
    },
    playerSpecialAttack(){
      let specialAttack = Math.floor(Math.random()  * (15-5) + 5);
      console.log("Special Attack has been used. " ,  specialAttack);
      this.monsterHealth = this.monsterHealth - specialAttack;
      this.battleLogs.push({type:'specialAttack', value:specialAttack})
      this.monsterAttack();
    },
    monsterAttack(){
      let attack = Math.floor(Math.random() * (13-4) + 4);
      console.log("Monster Performed an attack" , attack);
      this.playerHealth = this.playerHealth - attack;
      this.battleLogs.push({type:'monsterAttacking', value:attack})
    },
    playerHealing1(){
      let healing = Math.floor(Math.random() * (13-4) + 4 );
      this.playerHealth +=healing;
      if(this.playerHealth>100){
        this.playerHealth= 100;
      }
      this.battleLogs.push({type:'playerHealing', value:healing});
      this.monsterHealing();
    },
    monsterHealing(){
      let healing = Math.floor(Math.random() * (13-4) + 4 );
      this.monsterHealth +=healing;
      if(this.monsterHealth>100){
        this.monsterHealth= 100;
      }
      this.battleLogs.push({type:'monsterHealing', value:healing});
    },
    playerSurrender(){
      this.playerSurrenders=true;
      this.playerHealth=0;
      console.log('player has surrendered')
    },
    newGame(){
      this.playerSurrenders=false;
      this.playerHealth=100;
      this.monsterHealth=100;
      this.battleLogs=[];
      this.winner=null;
      this.gameOver=false;
    }
  },
  computed:{
  //   This one is for the style
    monsterBarStyles(){
      return {width:this.monsterHealth + '%'}
    },
    playerBarStyles() {
      return {width:this.playerHealth + '%'}
    }
  },
  watch:{
    playerHealth(value){
      if(value<=0 && this.monsterHealth<=0){
        //Draw
        this.gameOver=true;
        this.winner='draw'
      }
      else if(value<=0){
        this.winner='monster'
        this.gameOver=true;
      }
    },
    monsterHealth(value){
      if(value<=0 && this.playerHealth<=0){
        this.gameOver=true;
      }
      else if(value<=0){
        this.winner='player';
        this.gameOver=true;
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

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 0.5rem;
  background-color: #880017;
  color: white;
  text-align: center;
  margin-bottom: 2rem;
}

section {
  width: 90%;
  max-width: 40rem;
  margin: auto;
}

.healthbar {
  width: 100%;
  height: 40px;
  border: 1px solid #575757;
  margin: 1rem 0;
  background: #fde5e5;
}

.healthbar__value {
  background-color: #00a876;
  width: 100%;
  height: 100%;
}

.container {
  text-align: center;
  padding: 0.5rem;
  margin: 1rem auto;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  border-radius: 12px;
}

#monster h2,
#player h2 {
  margin: 0.25rem;
}

#controls {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}

button {
  font: inherit;
  border: 1px solid #88005b;
  background-color: #88005b;
  color: white;
  padding: 1rem 2rem;
  border-radius: 12px;
  margin: 1rem;
  width: 12rem;
  cursor: pointer;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

button:focus {
  outline: none;
}

button:hover,
button:active {
  background-color: #af0a78;
  border-color: #af0a78;
  box-shadow: 1px 1px 8px rgba(0, 0, 0, 0.26);
}

button:disabled {
  background-color: #ccc;
  border-color: #ccc;
  box-shadow: none;
  color: #3f3f3f;
  cursor: not-allowed;
}

#log ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

#log li {
  margin: 0.5rem 0;
}

.log--player {
  color: #7700ff;
}

.log--monster {
  color: #da8d00;
}

.log--damage {
  color: red;
}

.log--heal {
  color: green;
}
</style>