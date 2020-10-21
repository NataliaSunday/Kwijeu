<template>
 <div id="app">
     <button @click="isStarted = !isStarted">Start</button>
     <section v-if="isStarted === true">
        <question :content="quizData.questions[numberOfQuestion].content.question"></question>
        <answer :answer="quizData.questions[numberOfQuestion].content.answers"></answer>
     </section>
     <good-answer
     v-if="isAnswerGood"
     :question="quizData.questions[numberOfQuestion].content.question"
     :answer="quizData.questions[numberOfQuestion].content.answers.find(element => element.isTrue = true)"></good-answer>
 </div>
</template>

<script>
import json from './quiz-data.json'
import question from './components/Question.vue'
import answer from './components/Answer.vue'
import goodAnswer from './components/GoodAnswer.vue'

export default {
  data () {
    return {
      isStarted: false,
      quizData: json,
      numberOfQuestion: '1',
      isAnswerGood: true
    }
  },
  components: {
    question,
    answer,
    goodAnswer
  },
  mounted () {
    this.$root.$on('goodAnswer', () => {
      this.isAnswerGood = true
    })
  }
}
</script>

<style lang="scss">
</style>
