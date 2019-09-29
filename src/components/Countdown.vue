<template>
  <div class="cycle">
    <p class="countdown">{{ minutes }}:{{ seconds }}</p>
    <button v-if="!cycleRunning" @click="$emit('start')">{{ !cycleStarted ? "Start":"Resume" }}</button>
    <button v-if="cycleRunning" @click="$emit('pause')">Pause</button>
  </div>
</template>

<script>
export default {
  name: "Countdown",
  props: {
    cycleStarted: Boolean,
    cycleRunning: Boolean,
    cycleRemaining: Number
  },
  computed: {
    minutes() {
      return Math.floor(this.cycleRemaining / 60);
    },
    seconds() {
      const seconds = this.cycleRemaining % 60;
      // Add leading zero if needed
      return seconds < 10 ? "0" + seconds : seconds;
    }
  }
};
</script>