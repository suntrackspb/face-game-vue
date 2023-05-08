<template>
  <div>
    <AppGameCard
        :quest="question"
        :ans="answers"
        :quest_id="quest_id"
        @check-answer="checkAnswer"
        v-if="isVisible"
        :class="r_class"
    />
    <AppResults v-if="!isVisible" :results="result"/>
  </div>
</template>

<script>
import AppGameCard from "@/components/UI/AppGameCard.vue";
import axios from "axios";
import AppResults from "@/components/AppResults.vue";

export default {
  name: "AppGame",
  components: { AppResults, AppGameCard },
  props: {
    submittedName: String,
    game_id: String,
  },
  data() {
    return {
      quest_id: '',
      question: '',
      answers: [],
      isVisible: true,
      result: {},
      r_class: 'default'
    };
  },
  methods: {
    nextQuestion() {
      const data = {
        game_id: localStorage.game_id,
      }
      // console.log(data)
      const config = {
        headers: {
          'Content-Type': 'application/json'
        }
      }

      axios.post('http://192.168.0.100:5000/api/v1/question', data, config)
          .then(response => {
            // console.log(response.data)
            this.quest_id = response.data.quest_id
            this.question = response.data.question;
            this.answers = response.data.answers;
            if(response.data.status === 'end')
            {
              this.get_result()
            }
          })
          .catch(error => {
            console.error(error)
          })
    },
    get_result(){
      const data = {
        game_id: localStorage.game_id,
      }

      const config = {
        headers: {
          'Content-Type': 'application/json'
        }
      }

      axios.post('http://192.168.0.100:5000/api/v1/results', data, config)
          .then(response => {
            // console.log("RESULT RUN")
            // console.log(response.data)
            this.isVisible = false
            this.result = response.data
          })
          .catch(error => {
            console.error(error)
          })
    },
    checkAnswer(quest_id, answer) {
      const data = {
        game_id: localStorage.game_id,
        quest_id: quest_id,
        answer: answer,
      }

      const config = {
        headers: {
          'Content-Type': 'application/json'
        }
      }

      axios.post('http://192.168.0.100:5000/api/v1/answer', data, config)
          .then(response => {
            if(response.data.status === 'ok')
            {
              if(response.data.answer){
                this.r_class = 'true'
              } else {
                this.r_class = 'false'
              }
              setTimeout(() => {
                this.r_class = 'default'
                this.nextQuestion();
              }, 500);
            }
          })
          .catch(error => {
            console.error(error)
          })
    }
  },
  mounted() {
    setTimeout(() => {
      this.nextQuestion();
    }, 100);
  },
};
</script>

<style scoped>
.default {
  border: 5px solid #1d1e21;
}
.true {
  border: 5px solid #89d23b;
}
.false {
  border: 5px solid #d33b01;
}
</style>