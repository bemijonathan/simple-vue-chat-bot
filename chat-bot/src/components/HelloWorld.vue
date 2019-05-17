<template>
  <div class="hello">
    chat bot
    <div>
      <div v-for="(q, i) in questions" :key="i">
        <div v-if="i <= counter">
          <p>{{q.questions}}</p>
          <p>{{q.answers}}</p>
        </div>
      </div>
    </div>
    <input type="text" placeholder="answers" @change="getAnswer()" v-model="answer">
    <button>submit</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      botQuestion:[
         "what is your name",
        "ok, where do you stay ",
        ", wow thats a nice place \n welcome ",
        "ok, what do you want to buy"
      ],
      questions: [
        {id:1, questions: "what is your name", answers: "" },
        {id:2, questions:"", answers:''},
        {id:3, questions:"", answers:''},
        {id:4, questions:"", answers:''}
      ],
      counter: 0,
      answers: [],
      answer: ""
    };
  },
  methods: {
    getAnswer() {
      this.questions[this.counter].answers = this.answer;
      this.answers.push(this.answer)
      
      // if there are exceptions in the questions
      // if(this.counter === 1){
      //   this.questions[this.counter].questions = `${this.answer} ${this.botQuestion[this.counter]} ${this.answer}`
      //   this.counter++
      // }
      this.counter++;
      this.questions[this.counter].questions = `${this.answer} ${this.botQuestion[this.counter]}`
      this.answer = "";
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
