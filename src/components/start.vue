import { title } from 'process';

<template>
  <div>
    <h1 class="heading">
      {{ title }}
    </h1>
    <section id="monster" class="container">
      <h2>Monster Health</h2>
      <div class="healthbar">
        <div class="healthbar_value" :style="monsterBarStyles"></div>
      </div>
    </section>
    <section id="player" class="container">
        <h2>Your Health</h2>
        <div class="healthbar">
            <div class="healthbar_value" :style="playerBarStyles" ></div>
        </div>
        
    </section>
    <section id="controls">
        <button @click="attackMonster()">ATTACK</button>
        <button @click="specialAttackMonster()">SPECIAL ATTACK</button>
        <button @click="healPlayer()">HEAL</button>
    </section>

  </div>
</template>
<script>
export default {
  data() {
    return {
      title: "THE MONSTER GAME",
      playerHaelth:100,
      monsterHealth:100,

    };
  },
  computed:{
  monsterBarStyles()
  {
    return {width: this.monsterHealth + '%'};
  },
  playerBarStyles()
  {
    return {width: this.playerHaelth + '%'};
  }
  },
  methods:{
     attackMonster()
     {
        const attackValue=Math.floor(Math.random()*(5-10))+5
        this.monsterHealth =this.monsterHealth-attackValue
        this.attackplayer();
     },
     attackplayer()
     {
        const attackValue=Math.floor(Math.random()*(5-12))+5
        this.playerHaelth=this.playerHaelth-attackValue
        
     },
     specialAttackMonster()
     {
        const attackValue=Math.floor(Math.random()*(7-12))+5
        this.monsterHealth =this.monsterHealth-attackValue
        this.attackplayer();
     },
     healPlayer()
     {
        const healvalue =(Math.random()*(10-12))+2;
        if(this.playerHaelth + healvalue > 100)
        {
            this.playerHaelth=100;
        }
        else{
            this.playerHaelth +=healvalue
        }
        this.attackplayer();
     }
  }
};
</script>
<style scoped>
.heading {
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

.healthbar_value {
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
</style>
