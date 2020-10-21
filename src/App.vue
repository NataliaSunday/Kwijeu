<template>
 <div id="app">
     <button @click="isStarted = !isStarted">Start</button>
     <section v-if="isStarted === true">
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
    })
    this.$root.$on('badAnswer', () => {
      this.isAnswerGood = false
      this.showResult = true
    })
  }
}
</script>

<style lang="scss">
</style>
