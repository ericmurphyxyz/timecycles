<template>
  <div id="app">
    <Countdown :cycleRemaining="cycleRemaining" @start="startCycle" />
  </div>
</template>

<script>
import Countdown from "./components/Countdown";

export default {
  name: "app",
  components: {
    Countdown
  },
  data() {
    return {
      cycleRemaining: 3600
    };
  },
  methods: {
    startCycle() {
      this.cycleRemaining -= 1;
      setTimeout(this.startCycle, 1000);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
