<template>
<transition name="slide" appear>
      <section class="checkScreen flex--center" :style="[isGood ? {background: 'linear-gradient(var(--green) 40%, var(--white))'} : {background: 'linear-gradient(var(--red) 40%, var(--white))'}]">
        <article :style="[isGood ? {boxShadow: '0 .25rem .5rem var(--green)'} : {boxShadow: '0 .25rem .5rem var(--red'}]"
          class="checkScreen__box flex--center">
          <p
          :style="[isGood ? {color: 'var(--green)'} : {color: 'var(--red)'}]"
          class="checkScreen__box__question">{{ question }}</p>
          <p
          :style="[isGood ? {color: '#A7D18F'} : {color: '#DF9278'}]"
          class="checkScreen__box__answer">{{ answer.content }}</p>
        </article>
    </section>
  </transition>
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

<style scoped>
.checkScreen{
  position: absolute;
  top: 0;
  width: 100vw;
  height: 100vh;
}
.checkScreen__box{
  position: relative;
  transform: translateY(-25%);
  width: 20rem;
  height: 18rem;
  padding: .5rem;
  background-color: var(--white);
  border-radius: 1.5rem;
}
.checkScreen__box__question{
  font-size: 3rem;
  color: var(--green);
  text-align: center;
}
.checkScreen__box__answer{
  width: 100%;
  margin-top: .25rem;
  font-weight: 300;
  color: #A7D18F;
  font-size: 2rem;
  text-align: center;
}
.slide-enter{
  height: 0;
  opacity: 0;
}
.slide-enter-to{
}
.slide-enter-active, .slide-leave-active{
  transition: all 1s ease;
}
.slide-leave{
}
.slide-leave-to{
  height: 0;
  opacity: 0;
}

</style>
