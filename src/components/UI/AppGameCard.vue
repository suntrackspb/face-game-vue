<template>
  <div class="app-card">
    <img :src="'https://sntrk.ru/faces/' + quest + '.png'" />
    <div class="app-answers">
      <AppAnswerBtn
          v-for="answer in ans"
          :key="answer.id"
          @click="emitCheckAnswer(quest, answer)"
      >
        {{ answer }}
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
  props: {
    quest: Number,
    ans: Array,
  },
  methods: {
    emitCheckAnswer(id, name) {
      console.log(id, name)
      this.$emit('check-answer', id, name);
      this.$emit('next');
    }
  },
};
</script>

<style scoped>
.app-answers {
  display: flex;
}
img {
  width: 400px;
}
</style>


<!--{id: answer.id, answer: answer}-->
<!--@click="$emit('next')"-->