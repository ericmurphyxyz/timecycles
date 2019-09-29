<template>
  <div id="app">
    <BeforeCycle
      :cycleStarted="cycleStarted"
      :cycleRunning="cycleRunning"
      :cycleDefault="cycleDefault"
      @update="updateDefault"
    />
    <Countdown
      :cycleStarted="cycleStarted"
      :cycleRunning="cycleRunning"
      :cycleRemaining="cycleRemaining"
      @start="startCycle"
      @pause="pauseCycle"
    />
  </div>
</template>

<script>
import BeforeCycle from "./components/BeforeCycle";
import Countdown from "./components/Countdown";

export default {
  name: "app",
  components: {
    BeforeCycle,
    Countdown
  },
  data() {
    return {
      interval: null,
      cycleStarted: false,
      cycleRunning: false,
      cycleDefault: 1800,
      cycleRemaining: null
    };
  },
  created() {
    this.cycleRemaining = this.cycleDefault;
  },
  methods: {
    startCycle() {
      // Start work cycle if not started
      if (!this.cycleStarted) this.cycleStarted = true;
      // Set/resume cycle to running
      this.cycleRunning = true;
      this.interval = setInterval(this.continueCycle, 1000);
    },
    continueCycle() {
      if (this.cycleRemaining > 0) {
        this.cycleRemaining--;
      } else {
        this.resetCycle();
      }
    },
    pauseCycle() {
      // Clear interval from work cycle
      this.cycleRunning = false;
      clearInterval(this.interval);
    },
    updateDefault(newTime) {
      const newSeconds = newTime * 60;
      this.cycleDefault = newSeconds;
      this.cycleRemaining = newSeconds;
    },
    resetCycle() {
      this.cycleStarted = false;
      this.cycleRunning = false;
      clearInterval(this.interval);
      this.cycleRemaining = this.cycleDefault;
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
