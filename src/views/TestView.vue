<template>
  <div class="test">
    <h1>Test here</h1>
    <span v-bind:title="title">mouse hover for information</span>
    <CounterTimer class="demo"></CounterTimer>
    <ModelExample class="demo"></ModelExample>
    <WatchExample class="demo"></WatchExample>
    <TableExample class="demo"></TableExample>
  </div>
</template>

<script>
import CounterTimer from "../components/CounterTimer.vue";
import ModelExample from "@/components/ModelExample.vue";
import WatchExample from "@/components/WatchExample.vue";
import TableExample from "@/components/TableExample.vue";

export default {
  name: "TestView",
  components: {
    CounterTimer,
    ModelExample,
    WatchExample,
    TableExample,
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
  width: 70%;
  min-width: 800px;
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
