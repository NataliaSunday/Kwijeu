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
  box-shadow: 0 .25rem .5rem var(--orange);
  margin: .33rem 0;
}
.answer{
display: flex;
flex-direction: column;
}
</style>
