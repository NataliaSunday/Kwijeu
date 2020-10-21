<template>
    <section class="answer">
        <ul>
            <li v-for="el in answer" :key="el.id" @click="check(el.isTrue)">{{el.content}}</li>
        </ul>
    </section>
</template>

<script>

export default {
  props: {
    answer: Array
  },
  methods: {
    check (isTrue) {
      if (isTrue) {
        this.$root.$emit('goodAnswer')
      } else {
        this.$root.$emit('badAnswer')
      }
    }
  }
}
</script>

<style lang="sass">

</style>
