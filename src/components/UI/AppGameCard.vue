<template>
  <div class="app-card">
    <img :src="quest" :alt="quest_id"/>
    <div class="app-answers">
      <AppAnswerBtn
          v-for="answer in ans"
          :key="answer.id"
          @click="emitCheckAnswer(quest_id, answer)"
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
    quest: String,
    quest_id: String,
    ans: Array,
  },
  methods: {
    emitCheckAnswer(quest_id, name) {
      // console.log(quest_id, name)
      this.$emit('check-answer', quest_id, name);
    }
  },
};
</script>

<style scoped>
.app-card {
  margin: 30px;
  /*background: #333;*/
  border-radius: 20px;
}
.app-answers {
  width: 100%;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;

}
img {
  width: 100%;
  border-radius: 10px 10px 0 0;
  display: block;
}
@media(min-width: 600px) {
  .app-card {
    width: 500px;
  }
  .app-answers {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
  }
}

@media(max-width: 600px) {
  .app-answers {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-between;
  }
  .app-ans-button:hover {
    background: #7a7a7a;
    color: white;
  }

  .app-ans-button:active {
    background: #3b77d2;
    color: white;
    transition: all 0.01s ease;
  }
}
</style>


<!--{id: answer.id, answer: answer}-->
<!--@click="$emit('next')"-->