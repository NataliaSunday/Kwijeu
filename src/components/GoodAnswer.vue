<template>
    <article>
        {{ question }}
        {{ answer.content }}
    </article>
</template>

<script>
export default {
  props: {
    question: String,
    answer: String
  }
}
</script>

<style lang="sass">

</style>
