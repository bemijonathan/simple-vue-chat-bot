<template>
  <div>
    chaxbox
    <div v-for="(ques, i) in botQuestion" :key="i">
      <div v-if="counter >= i ">
        <p class="bot">{{ques.question}}</p>
        <p class="user">{{ques.answer}}</p>
      </div>
    </div>

    <form @submit.prevent="submit()">
      <input v-if="botQuestion[counter].option.length === 0 && counter != 6" v-model="answer">
      <select v-if="botQuestion[counter].option.length > 0" v-model="answer">
        <option v-for="value in botQuestion[counter].option" :key="value" :value="value">{{value}}</option>
      </select>
      <input type="file" v-if="counter === 6">

      <button>submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      botQuestion: [
        { question: "what is your name", option: [] },
        { question: "ok, where do you stay ", option: [] },
        { question: ", wow thats a nice place \n welcome ", option: [] },
        { question: "ok, what do you want to buy", option: ["bags"] },
        { question: "gender ??", option: ["male", "female"] },
        { question: "categories", option: ["bags", "shoes", "clothings"] },
        { question: "logo??", option: [] }
      ],
      counter: 0,
      answer: ""
    };
  },
  methods: {
    submit() {
      if (this.counter < this.botQuestion.length) {
        setTimeout(() => {
          this.next();
        }, 1000);
      }else{
        console.log(this.botQuestion)
      }
    },
    next() {
      this.botQuestion[this.counter].answer = this.answer;
      this.counter++;
      this.answer = "";
    }
  }
};
</script>

<style>
.bot {
  background: aqua;
  max-width: 200px;
  margin-left: auto;
}
.user {
  background: red;
  max-width: 200px;
  color: white;
  margin-right: auto;
}
</style>
