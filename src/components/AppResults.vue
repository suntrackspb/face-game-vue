<template>
  <div class="app__answer-wrapper">
    <h1>Время: {{ time_count() }}</h1>
    <div class="app__answer-container">
      <div class="app__answer-result"><p>Вы ответили верно на <strong>{{count_correct_answers}}</strong> из <strong>{{count_answers}}</strong> вопросов</p></div>
<!--      <div class="app__answer-item" v-for="(i, index) in results.answers" :key="index">-->
<!--        {{ index + 1 }}.<span :class="i.answer ? 'green' : 'red'"> {{ i.answer ? 'Верно' : 'Неверно' }}</span>-->
<!--      </div>-->
    </div>
    <AppButton @click="reload">Ещё раз?</AppButton>
  </div>
</template>

<script>
import AppButton from "@/components/UI/AppButton";
export default {
  name: "AppResults",
  components: {AppButton},
  data() {
    return {
      count_answers: this.results.answers.length,
      count_correct_answers: 0
    }
  },
  props: {
    results: Object,
  },
  methods: {
    time_count() {
      let t_start = new Date(this.results.time_start);
      let t_end = new Date(this.results.time_end);
      let timeInMillis = t_end - t_start;
      return `${Math.floor(timeInMillis / 1000 / 60)} мин ${Math.floor(timeInMillis / 1000 % 60)} сек`;
    },
    reload(){
      window.location.reload();
    }
  },
  mounted() {
    // console.log(this.results);
    const answers = this.results.answers
    answers.forEach(elem => {
      if (elem.answer) {
        this.count_correct_answers++
      }
    })
  }
};
</script>
<style scoped>
.app__answer-wrapper {
  max-width: 342px;
}
.app__answer-item {
  margin: 5px;
}
.app__answer-result {
  margin: 10px 0;
}
.app__answer-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  margin: 10px;
}
.green {
  color: green;
  padding: 5px;
}

.red {
  color: red;
  padding: 5px;
}
</style>