<template>
  <div class="popup">
    <h1> You became a turtle! </h1>
    <h2 v-if="this.clicks === 1"> After {{clicks}} click, you were turned into a turtle with a net worth of ${{money}}. </h2>
    <h2 v-else> After {{clicks}} clicks, you were turned into a turtle with a net worth of ${{money}}. </h2>
    <h2> Was it worth it? </h2>
    <button @click="newGame"> Play Again </button>
  </div>
</template>

<script>
export default {
  name: "PopUp",
  props: {
    clicks: {
      type: Number,
      required: true,
      default: 0,
    },
    money: {
      type: Number,
      required: true,
      default: 0,
    }
  },
  methods: {
    newGame() {
      this.$emit('reset');
    }
  }
}
</script>

<style scoped>
.popup {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 50%;
  position: absolute;
  background: white;
  color: black;
  border-radius: 5px;
  padding: 1rem;
  top: 25%;
  left: 25%;
  text-align: center;
  box-shadow: rgba(0,0,0,0.25) 5px 5px 5px;
  z-index: 3
}
</style>
