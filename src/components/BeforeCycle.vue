<template>
  <label v-if="!cycleStarted">
    How many minutes for your work cycle?
    <select @change="$emit('update', $event.target.value)">
      <option
        v-for="(time,index) in times"
        :value="time"
        :key="index"
        :selected="time === defaultTime"
      >{{ time }}</option>
    </select>
  </label>
</template>

<script>
export default {
  name: "BeforeCycle",
  data() {
    return {
      times: [15, 20, 25, 30, 35, 40, 45, 50, 55, 60]
    };
  },
  props: {
    cycleStarted: Boolean,
    cycleRunning: Boolean,
    cycleRemaining: Number
  },
  computed: {
    defaultTime() {
      return Math.floor(this.cycleRemaining / 60);
    }
  }
};
</script>