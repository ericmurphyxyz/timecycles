<template>
  <div class="cycle">
    <span class="countdown">{{ cycleRemaining }}</span>
    <button @click="$emit('start')">Start</button>
  </div>
</template>

<script>
export default {
  name: "Countdown",
  props: {
    cycleRemaining: Number
  }
};
</script>

<style>
</style>