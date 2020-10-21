<template>
 <div id="app">
     <button @click="isStarted = !isStarted">Start</button>
     <section v-if="isStarted === true">
        <question :content="quizData.questions[numberOfQuestion].content.question"></question>
        <answer :answer="quizData.questions[numberOfQuestion].content.answers">
        </answer>
     </section>
 </div>
</template>

<script>
import json from './quiz-data.json'
import question from './components/Question.vue'
import answer from './components/Answer.vue'

export default {
  data () {
    return {
      isStarted: false,
      quizData: json,
      numberOfQuestion: '1'
    }
  },
  components: {
    question,
    answer
  }
}
</script>

<style lang="scss">
</style>
