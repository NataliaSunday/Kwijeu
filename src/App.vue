<template>
 <div id="app">
  <transition name="up" appear>
    <section v-if="!isStarted" class="welcomeScreen flex--center">
      <button @click="isStarted = !isStarted" class="btn btn--primary">start quiz</button>
    </section>
  </transition>
  <transition name="up">
    <section v-if="isStarted === true" class="quizScreen flex--center">
      <question :content="quizData.questions[numberOfQuestion].content.question"></question>
      <answer :answer="quizData.questions[numberOfQuestion].content.answers"></answer>
  </section>
  </transition>
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
      }, 2500)
    })
    this.$root.$on('badAnswer', () => {
      this.isAnswerGood = false
      this.showResult = true
      setTimeout(() => {
        this.showResult = false
        this.numberOfQuestion = Math.floor(Math.random() * 5)
      }, 2500)
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
  background: linear-gradient(#4CBBE0 ,var(--blue) 40%, var(--white));
}
.quizScreen{
  width: inherit;
  height: inherit;
  background: linear-gradient(var(--orange) 40%, var(--white));
}
.btn{
  width: 20rem;
  height: min-content;
  padding: .5em;
  border-radius: .55rem;
  border: 1px var(--white);
  background-color: var(--white);
  font-family: 'Lato','Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
  font-size: 1.75rem;
  font-weight: 300;
  outline: none;
}
.btn--primary{
  color: var(--blue);
  box-shadow: 0 .25em .5em var(--blue);
}
.flex--center{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.up-enter{
  opacity: 0;
  height: 0%;
}
.up-enter-to{
  opacity: 1;
  height: 100%;
}
.up-enter-active{
  transition: all 1s ease;
}
.up-leave-active{
   transition: all 1s ease;
}
.up-leave{
  opacity: 1;
  height: 100%;
}
.up-leave-to{
  opacity: 0;
  height: 0%;
}
</style>
