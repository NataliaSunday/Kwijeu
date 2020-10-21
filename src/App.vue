<template>
 <div id="app">
   {{quizData.questions[1].content}}
   <hr>
   {{quizData.questions[1]}}
   <hr>
    {{quizData.questions}}
     <button @click="isStarted = !isStarted">Start</button>
     <section v-if="isStarted === true">
        <question></question>
     </section>
 </div>
</template>

<script>
import json from './quiz-data.json'
import question from './components/Question.vue'

export default {
  data () {
    return {
      isStarted: false,
      quizData: json,
      numberOfQuestion: '1'
    }
  },
  components: {
    question
  }
}
</script>

<style lang="scss">
</style>
