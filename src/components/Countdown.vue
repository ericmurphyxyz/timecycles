<template>
  <div class="cycle">
    <p class="countdown">{{ cycleRemaining }}</p>
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
  }
};
</script>

<style>
</style>