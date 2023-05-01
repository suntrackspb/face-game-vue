<template>
  <div class="app-card">
    <img src="" alt="">
    <div class="app-answers">
      <AppAnswerBtn v-for="answer in answers" :key="answer.id">
        {{ answer.text }}
      </AppAnswerBtn>
    </div>
  </div>
</template>

<script>
import AppAnswerBtn from "@/components/UI/AppAnswerBtn.vue";

export default {
  name: "AppGameCard",

  components: {
    AppAnswerBtn
  },

  data() {
    return {
      answers: [
        {id: 1, text: 'Ответ 1'},
        {id: 2, text: 'Ответ 2'},
        {id: 3, text: 'Ответ 3'},
        {id: 4, text: 'Ответ 4'},
      ]
    }
  },
};
</script>

<style scoped>
.app-answers {
  display: flex;
}
</style>