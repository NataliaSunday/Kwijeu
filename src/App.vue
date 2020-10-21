<template>
 <div id="app">
     <button @click="isStarted = !isStarted">Start</button>
     <section v-if="isStarted === true">
        <div ></div>
     </section>
 </div>
</template>

<script>
import json from './quiz-data.json'

export default {
  data () {
    return {
      isStarted: false,
      quizData: json
    }
  }
}
</script>

<style lang="scss">
</style>
