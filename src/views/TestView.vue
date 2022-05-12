<template>
  <div class="test">
    <h1>Test here</h1>
    <span :title="title">mouse hover for information</span>
    <div class="demo">
      <p>Counter: {{ counter }}</p>
      <button v-if="interval != null" :onClick="stopTimer">Stop Timer</button>
      <button v-else :onClick="startTimer">Start Timer</button>
    </div>
  </div>
</template>

<script>
export default {
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
  computed: {
    title() {
      return "you load this page on " + new Date().toLocaleString();
    },
  },
};
</script>

<style scoped>
.test {
  width: 60%;
  max-width: 740px;
  margin: auto;
}

.demo {
  border: 1px solid #eee;
  border-radius: 2px;
  padding: 20px 30px;
  margin-top: 1em;
  margin-bottom: 1px;
}
</style>
