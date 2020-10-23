<template>
    <section class="question">
        <p>{{ content }}</p>
    </section>
</template>

<script>

export default {
  props: {
    content: String
  }
}
</script>

<style>
.question{
  width: auto;
  height: auto;
  font-size: 3.5em;
  color: var(--white);
  margin-bottom: 1.5em;
}
</style>
