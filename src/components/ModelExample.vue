<template>
  <div>
    <ul>
      <li v-bind:key="index" v-for="(msg, index) in message.split('\n')">
        {{ msg }}
      </li>
    </ul>
    <textarea v-model="message" />
  </div>
</template>

<script>
export default {
  name: "ModelExample",
  data() {
    return {
      message: "1. two way binding example\n2. v-for example",
    };
  },
};
</script>

<style>
textarea {
  width: 60%;
}

li {
  margin: auto;
  text-align: left;
  width: 60%;
}
</style>
