<template>
    <section class="answer">
        <ul>
            <li v-for="el in answer" :key="el.id">{{el.content}}</li>
        </ul>
    </section>
</template>

<script>

export default {
  props: {
    answer: Array
  }
}
</script>

<style lang="sass">

</style>
