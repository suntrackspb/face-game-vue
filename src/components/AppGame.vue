<template>
  <div>
<!--    <h1>{{ submittedName }}</h1>-->
<!--    <h1>Game is ready!</h1>-->
    <AppGameCard
        :quest="question"
        :ans="answers"
        @next="nextQuestion"
        @check-answer="checkAnswer"
        v-if="isVisible"
    />
    <AppResults v-if="!isVisible" :res="result"/>
  </div>
</template>

<script>
import AppGameCard from "@/components/UI/AppGameCard.vue";
import axios from "axios";
import AppResults from "@/components/UI/AppResults.vue";

export default {
  name: "AppGame",
  components: {AppResults, AppGameCard },
  props: {
    submittedName: String,
  },
  data() {
    return {
      question: 0,
      answers: [],
      isVisible: true,
      result: []
    };
  },
  methods: {
    nextQuestion() {
      const data = {
        name: localStorage.name,
      }

      const config = {
        headers: {
          'Content-Type': 'application/json'
        }
      }

      axios.post('http://192.168.0.100:5000/api/v1/question', data, config)
          .then(response => {
            console.log(response.data)
            this.question = response.data.id;
            this.answers = response.data.names;
          })
          .catch(error => {
            console.error(error)
          })
    },

    checkAnswer(id, answer) {
      const data = {
        name: localStorage.name,
        id: id,
        answer: answer,
      }

      const config = {
        headers: {
          'Content-Type': 'application/json'
        }
      }

      axios.post('http://192.168.0.100:5000/api/v1/answer', data, config)
          .then(response => {
            console.log(response.data)
            if(response.data.status === 'end')
            {
              this.isVisible = false
              this.result = response.data.result
            }
          })
          .catch(error => {
            console.error(error)
          })
    }
  },
  created() {
    this.nextQuestion()
  },
};
</script>

<style scoped>

</style>