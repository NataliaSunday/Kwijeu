<template>
    <article  :style="[isGood ? {backgroundColor: 'green'} : {backgroundColor: 'red'}]">
        {{ question }}
        {{ answer.content }}
    </article>
</template>

<script>
export default {
  props: {
    question: String,
    answer: String,
    isGood: Boolean
  }
}
</script>

<style>

</style>
