<template>
  <div>
    <p>Counter: {{ counter }}</p>
    <button v-if="interval != null" v-on:click="stopTimer">Stop Timer</button>
    <button v-else v-on:click="startTimer">Start Timer</button>
  </div>
</template>

<script>
export default {
  name: "CounterTimer",
  data() {
    return {
      counter: 0,
      interval: null,
      myTimer: () => {
        return setInterval(() => {
          this.counter += 1;
        }, 1000);
      },
    };
  },
  mounted() {
    this.interval = this.myTimer();
  },
  methods: {
    stopTimer() {
      clearInterval(this.interval);
      this.interval = null;
    },
    startTimer() {
      this.interval = this.myTimer();
    },
  },
};
</script>
