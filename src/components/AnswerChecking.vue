<template>
    <section class="checkScreen" :style="[isGood ? {background: 'linear-gradient(var(--green) 40%, var(--white))'} : {background: 'linear-gradient(var(--red) 40%, var(--white))'}]">
        <article   :style="[isGood ? {boxShadow: '0 .25em .5em var(--green)'} : {boxShadow: '0 .25em .5em var(--red'}]"
        class="checkScreen__box">
          <p
          :style="[isGood ? {color: 'var(--green)'} : {color: 'var(--red)'}]"
          class="checkScreen__box__question">{{ question }}</p>
          <p
          :style="[isGood ? {color: '#A7D18F'} : {color: '#DF9278'}]"
          class="checkScreen__box__answer">{{ answer.content }}</p>
        </article>
    </section>
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
.checkScreen{
  position: absolute;
  top: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
.checkScreen__box{
  position: relative;
  transform: translateY(-25%);
  width: 25em;
  height: 21em;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: var(--white);
  border-radius: 1.5em;
}
.checkScreen__box__question{
  font-size: 3.5em;
  color: var(--green);
}
.checkScreen__box__answer{
  width: 100%;
  margin-top: .25em;
  font-weight: 300;
  color: #A7D18F;
  font-size: 2em;
  text-align: center;
}
</style>
