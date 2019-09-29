<template>
  <div id="app">
    <Countdown
      :cycleRunning="cycleRunning"
      :cycleRemaining="cycleRemaining"
      @start="startCycle"
      @pause="pauseCycle"
    />
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
      interval: null,
      cycleRunning: false,
      cycleRemaining: 3600
    };
  },
  methods: {
    startCycle() {
      this.cycleRunning = true;
      this.interval = setInterval(this.continueCycle, 1000);
    },
    continueCycle() {
      this.cycleRemaining--;
    },
    pauseCycle() {
      this.cycleRunning = false;
      clearInterval(this.interval);
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
