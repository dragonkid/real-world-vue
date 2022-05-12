<template>
  <div class="test">
    <h1>Test here</h1>
    <span v-bind:title="title">mouse hover for information</span>
    <div class="demo">
      <CounterTimer></CounterTimer>
    </div>
    <div class="demo">
      <ModelExample></ModelExample>
    </div>
  </div>
</template>

<script>
import CounterTimer from "../components/CounterTimer.vue";
import ModelExample from "@/components/ModelExample.vue";

export default {
  name: "TestView",
  components: {
    CounterTimer,
    ModelExample,
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
