<template>
 <div id="app">
   <section v-if="!isStarted" class="welcomeScreen">
       <button @click="isStarted = !isStarted" class="btn btn--primary">start quiz</button>
   </section>
    <section v-if="isStarted === true" class="quizScreen">
        <question :content="quizData.questions[numberOfQuestion].content.question"></question>
        <answer :answer="quizData.questions[numberOfQuestion].content.answers"></answer>
     </section>
     <answer-checking v-if="showResult"
     :isGood="isAnswerGood"
     :question="quizData.questions[numberOfQuestion].content.question"
     :answer="quizData.questions[numberOfQuestion].content.answers.find(element => element.isTrue = true)"></answer-checking>
 </div>
</template>

<script>
import json from './quiz-data.json'
import question from './components/Question.vue'
import answer from './components/Answer.vue'
import answerChecking from './components/AnswerChecking.vue'

export default {
  data () {
    return {
      isStarted: false,
      quizData: json,
      numberOfQuestion: '1',
      isAnswerGood: '',
      showResult: ''
    }
  },
  components: {
    question,
    answer,
    answerChecking
  },
  mounted () {
    this.$root.$on('goodAnswer', () => {
      this.isAnswerGood = true
      this.showResult = true
      setTimeout(() => {
        this.showResult = false
        this.numberOfQuestion = Math.floor(Math.random() * 5)
      }, 1000)
    })
    this.$root.$on('badAnswer', () => {
      this.isAnswerGood = false
      this.showResult = true
      setTimeout(() => {
        this.showResult = false
        this.numberOfQuestion = Math.floor(Math.random() * 5)
      }, 1000)
    })
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
:root {
  --green: #7BC950;
  --white: #FFFFFC;
  --blue: #2BBFF0;
  --orange: #FF7F11;
  --red: #FF3F00;
}
#app{
  font-family: 'Lato','Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
  width: 100vw;
  height: 100vh;
}
.welcomeScreen{
  width: inherit;
  height: inherit;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(#4CBBE0 ,var(--blue) 40%, var(--white));
}
.quizScreen{
  width: inherit;
  height: inherit;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: linear-gradient(var(--orange) 40%, var(--white));
}
.btn{
  width: 14em;
  height: 2em;
  border-radius: .55em;
  border: 1px var(--white);
  background-color: var(--white);
  font-family: 'Lato','Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
  font-size: 1.75em;
  font-weight: 300;
  outline: none;
}
.btn--primary{
  color: var(--blue);
  box-shadow: 0 .25em .5em var(--blue);
}
</style>
