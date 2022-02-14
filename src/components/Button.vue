<template>
  <button class="button" :disabled="isDisabled" @click="click"/>
  <div class="base"/>
</template>

<script>
export default {
  name: "Button",
  props: {
    disabled: {
      type: Boolean,
      required: true,
      default: false
    }
  },
  computed: {
    isDisabled() {
      return this.disabled;
    }
  },
  methods: {
    click() {
      this.$emit('click');
    }
  }
}
</script>

<style scoped>
.button {
  position: absolute;
  background: #c33838;
  width: 300px;
  height: 200px;
  border: none;
  border-radius: 50%;
  box-shadow: #e15b65 0px 25px 0px;
  z-index: 2;
  cursor: pointer;
}

.base {
  position: relative;
  top: 25px;
  background: #676767;
  width: 350px;
  height: 250px;
  border-radius: 50%;
  box-shadow: #e0e0e0 0px 25px 0px;
  z-index: 1;
}
</style>
