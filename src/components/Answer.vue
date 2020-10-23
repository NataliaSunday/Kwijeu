<template>
    <section class="answer">
      <button class="btn btn--answer" v-for="el in answer" :key="el.id" @click="check(el.isTrue)">{{el.content}}</button>
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

<style>
.btn--answer{
  color: var(--orange);
  box-shadow: 0 .25em .5em var(--orange);
  margin: .2em 0;
}
.answer{
display: flex;
flex-direction: column;
}
</style>
