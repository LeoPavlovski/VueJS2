  <template>
  <div>
    <header>
      <h1>Monster Slayer</h1>
    </header>
    <div id="game">
      <section id="monster" class="container">
        <h2>Monster Health</h2>
        <div class="healthbar">
<!-- Css property, we need to add a unit.-->
          <div class="healthbar__value" :style="monsterBarStyles"></div>
        </div>
      </section>
      <section id="player" class="container">
        <h2>Your Health</h2>
        <div class="healthbar">
          <div class="healthbar__value" :style="playerBarStyles"></div>
        </div>
      </section>

<!--      <p v-if="this.monsterHealth>this.playerHealth">Monster is Leading</p>-->
<!--      <p v-else-if="this.monsterHealth === this.playerHealth">Start!</p>-->
<!--      <p v-else>Player is leading!</p>-->
       <section class="container" v-if="winner && gameOver===true">
         <h2>Game Over!</h2>
         <h3 v-if="winner==='player'">Player Won!</h3>
         <h3 v-if="winner==='monster'">Monster Won!</h3>
         <h3 v-if="winner==='draw'">It's a Draw!</h3>
           <button @click="setNewGame">Play New Game!</button>
       </section>

<!--      Remove All of the buttons if the player Surrenders-->
<!--      Remove all of the buttons if it's game over.-->

      <div v-if="playerSurrendered ===false && winner==null">
        <section id="controls">
          <button v-on:click="humanAttacking()">ATTACK</button>
          <!--ostatokot.-->
          <button :disabled="currentRound %3 !==0" v-on:click="specialAttack()" class="disabled  ">SPECIAL ATTACK</button>
          <button v-on:click="playerHealing()">HEAL</button>
          <button v-on:click="playerSurrenders()">SURRENDER</button>
        </section>
      </div>
      <section id="log" class="container">
        <h2>Battle Log</h2>
        <div v-for="monsterAttack in monsterAttacks" v-bind:key="monsterAttack">
          <div v-for="playerAttack in playerAttacks" v-bind:key="playerAttack">
              <ul>
                <li>Monster Attacks for : {{monsterAttack}} Hits!</li>
                <li>Player Attacks for : {{playerAttack}} Hits!</li>
              </ul>
        </div>
        </div>
      </section>
    </div>
  </div>
  </template>

  <script>
``
  export default{
    data(){
      return{
        specialAttacks:[],
        monsterAttacks:[],
        playerAttacks:[],
        monsterHealth:100,
        playerHealth:100,
        playerSurrendered:false,
        surrender:'',
        currentRound:0,
        newGame:false,
        winner:null,
        gameOver:false,
      }
    },
    methods:{
      humanAttacking(){
      let AttackValue =  Math.floor(Math.random() * (12-5)) + 5;
      this.currentRound++;
        console.log('Human Attacks For : ', AttackValue)
      this.monsterHealth = this.monsterHealth- AttackValue;
        this.playerAttacks.push(AttackValue);
      this.monsterAttacking();
      },
      specialAttack(){
        this.currentRound++;

        let specialAttack = Math.floor(Math.random() * (20-10) + 10);
        console.log('Human Attacks For : ', specialAttack)
       this.specialAttacks.push(specialAttack);
        this.monsterHealth = this.monsterHealth- specialAttack;
        this.monsterAttacking();
      },
      monsterAttacking(){
        let AttackValue = Math.floor(Math.random()* (15-8) + 5);
        console.log('Monster Attacks for : ', AttackValue)
        this.monsterAttacks.push(AttackValue);
        this.playerHealth = this.playerHealth- AttackValue;
      },
      setNewGame(){
      this.newGame=true;
      this.specialAttacks = [];
      this.monsterAttacks= [];
      this.playerAttacks= [];
      this.playerHealth = 100;
      this.monsterHealth = 100;
      this.playerSurrendered=false;
      this.currentRound= 0;
      this.winner=null;
      },
      playerHealing(){
        this.currentRound++;
        let Healing = Math.floor(Math.random() * (20 -10) + 5);
        this.playerHealth +=Healing;
        if(this.playerHealth>100){
          this.playerHealth=100;
        }
        console.log('Player healed for  : ' , Healing);
        this.monsterHealing()
      },
      monsterHealing(){
        let monsterHealing = Math.floor(Math.random() * (30-15) + 5);
        this.monsterHealth += monsterHealing;
        if(this.monsterHealth >=100){
          this.monsterHealth=100;
        }
        if(this.monsterHealth>100){
          //Display a message here that he cant heal more than 100 hp.
        }
        console.log('Monster healed for : ', monsterHealing);
      },
      playerSurrenders(){
        this.playerSurrendered=true;
        this.playerHealth=0;
        return 'Monster wins!'
      }
    },
    computed:{
      monsterBarStyles(){
        return {width:this.monsterHealth + '%'}
      },
      playerBarStyles(){
        return {width:this.playerHealth + '%'}
      }
    },
    watch:{
     playerHealth(value){
        if(value<=0 && this.monsterHealth<=0){
          //Draw
          this.winner='draw'
          this.gameOver=true;

          // this.playerHealth=0;
          // this.monsterHealth=0;
        }
        else if(value<=0){
          //Player lost
          this.winner='monster'
          this.gameOver=true;
          // this.playerHealth=0;
        }
      },
      monsterHealth(value){
      if(value<0 && this.playerHealth<=0){
       this.winner='draw'
        this.gameOver=true;
       // this.playerHealth=0;
       // this.monsterHealth=0;
      }
      else if(value<=0){
        this.winner='player'
        this.gameOver=true;
        this.monsterHealth=0;
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