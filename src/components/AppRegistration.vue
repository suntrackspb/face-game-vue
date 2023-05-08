<template>
  <AppNotify v-if="show" :message="message" :delay="3000" />
  <div class="app-content">
    <AppInput
        aria-placeholder="Enter name"
        placeholder="Enter name"
        ref="input"
    />
    <AppSelector ref="select" @change="getCount"/>
    <AppRange  :max-value="maxValue" ref="range" />
    <AppButton id="btn" @click="submitData">Start Game</AppButton>
  </div>
</template>


<script>
import AppButton from "@/components/UI/AppButton.vue";
import AppNotify from "@/components/UI/AppNotify";
import AppInput from "@/components/UI/AppInput.vue";
import axios from "axios";
import AppSelector from "@/components/UI/AppSelector.vue";
import AppRange from "@/components/UI/AppRange";

export default {
  name: "AppRegistration",
  components: {AppRange, AppSelector, AppInput, AppButton, AppNotify },
  emits: ['visible', 'handleSubmit'],
  data() {
    return {
      maxValue: 0,
      show: false,
      message: 'Выберите категорию.'
    }
  },
  methods: {
    showNotification() {
      this.show = true
    },
    submitData() {

      localStorage.name = this.$refs.input.inputValue
      if (this.$refs.select.selectValue !== 'null'){
        this.sendStart(this.$refs.input.inputValue, this.$refs.select.selectValue)
        this.$emit('visible');
      } else {
        this.showNotification()
      }
    },
    sendStart(name, category) {
      const data = {
        name: name,
        category: category,
        length: this.$refs.range.rangeValue
      }

      const config = {
        headers: {
          'Content-Type': 'application/json'
        }
      }

      axios.post('http://192.168.0.100:5000/api/v1/start', data, config)
      .then(response => {
        // console.log(response.data)
        localStorage.game_id = response.data.game_id
        this.$emit("visible", {
          inputValue: this.$refs.input.inputValue,
          selectValue: this.$refs.select.selectValue,
          game_id: response.data.game_id
        });
      })
      .catch(error => {
        console.error(error)
        return false
      })
    },
    getCount() {
      // console.log(this.$refs.select.selectValue)
      if(this.$refs.select.selectValue){
        const data = {
          category: this.$refs.select.selectValue
        }

        const config = {
          headers: {
            'Content-Type': 'application/json'
          }
        }

        axios.post('http://192.168.0.100:5000/api/v1/count', data, config)
        .then(response => {
          // console.log(response.data.count)
          this.maxValue = response.data.count

        })
        .catch(error => {
          console.error(error)
          return false
        })
      }
    }
  },
};
</script>

<style scoped>
.app-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 30px;
}
</style>