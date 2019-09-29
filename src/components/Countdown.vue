<template>
  <div class="cycle">
    <p class="countdown">{{ minutes }}:{{ seconds }}</p>
    <button v-if="!cycleRunning" @click="$emit('start')">Start</button>
    <button v-if="cycleRunning" @click="$emit('pause')">Pause</button>
  </div>
</template>

<script>
export default {
  name: "Countdown",
  props: {
    cycleRunning: Boolean,
    cycleRemaining: Number
  },
  computed: {
    minutes() {
      return Math.floor(this.cycleRemaining / 60);
    },
    seconds() {
      const seconds = this.cycleRemaining % 60;
      return seconds < 10 ? "0" + seconds : seconds;
    }
  }
};
</script>

<style>
</style>