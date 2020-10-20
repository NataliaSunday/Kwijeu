<template>
 <div id="app">
     <button @click="isStarted = !isStarted">Start</button>
     <section v-if="isStarted === true">
        <p>lalal</p>
     </section>
 </div>
</template>

<script>
export default {
  data () {
    return {
      isStarted: false
    }
  }
}
</script>

<style lang="scss">
</style>
