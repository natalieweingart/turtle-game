<template>
  <div class="app">
    <div class="header">
      <h1> Welcome to Turtle Game </h1>
      <h2> If you click the button there is a 99% chance you will win $25,000 </h2>
      <h2> However, there is also a 1% chance that you will turn into a turtle </h2>
      <h2> How many times will you press the button? </h2>
    </div>
    <div class="button">
      <Button @click="click" :disabled="disabled"/>
    </div>
    <div class="stat-box">
      <div class="click-count">
        <h2> Total Clicks: {{ clicks }} </h2>
      </div>
      <div class="money-count">
        <h2> Total Money: ${{ money }} </h2>
      </div>
    </div>
    <PopUp :clicks="clicks" :money="money" @reset="reset" v-if="active"/>
  </div>
</template>

<script>
import Button from "./components/Button.vue";
import PopUp from "./components/PopUp.vue";

export default {
  name: "App",
  components: {
    Button,
    PopUp,
  },
  data() {
    return {
      clicks: 0,
      money: 0,
      risk: 0,
      active: false,
      disabled: false,
    }
  },
  methods: {
    click() {
      this.clicks += 1;
      this.risk = Math.random();
      // if (this.turtleChance <= 0.01) {
      if (this.risk <= 0.01) {
        this.active = true;
        this.disabled = true;
      } else {
        this.addMoney();
      }
    },
    addMoney() {
      //TODO
      // Trigger display of "You got $25,000!"
      this.money += 25000
    },
    reset() {
      this.clicks = 0;
      this.money = 0;
      this.active = false;
      this.disabled = false;
    }
  },
}
</script>

<style>
@import './assets/base.css';

#app {
  width: 100vw;
  height: 100vh;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}

.app {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}

.header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  font-weight: bold;
}

.stat-box {
  display: flex;
  flex-direction: row;
}

.click-count {
  padding: 1rem;
}

.money-count {
  padding: 1rem;
}

.button {
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>
