<template>
  <div>
    <p>Ask a yes/no question: <input v-model="question" /></p>
    <p>{{ answer }}</p>
    <img :src="answerImage" />
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "WatchExample",
  data() {
    return {
      answer: "",
      answerImage: "",
      question: "question must end with question mark",
    };
  },
  watch: {
    // eslint-disable-next-line no-unused-vars
    question(newQuestion, oldQuestion) {
      if (newQuestion.endsWith("?")) {
        this.getAnswer();
      }
    },
  },
  methods: {
    getAnswer() {
      this.answer = "thinking...";
      this.answerImage = "";
      axios
        .get("https://yesno.wtf/api")
        .then((response) => {
          this.answer = response.data.answer;
          this.answerImage = response.data.image;
        })
        .catch((error) => {
          this.answer = error;
        });
    },
  },
};
</script>

<style>
input {
  width: 300px;
}
</style>
