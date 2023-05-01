<template>
  <div class="app-content">
    <AppInput
        aria-placeholder="Enter name"
        placeholder="Enter name"
        ref="input"
    />
    <AppButton @click="submitData">Start Game</AppButton>
  </div>
</template>

<script>
import AppButton from "@/components/UI/AppButton.vue";
import AppInput from "@/components/UI/AppInput.vue";
import axios from "axios";

export default {
  name: "AppRegistration",
  components: { AppInput, AppButton },
  methods: {
    submitData() {
      this.$emit("visible", {
        data: false,
        inputValue: this.$refs.input.inputValue,
      });
      this.sendStart(this.$refs.input.inputValue)
    },
    sendStart(name) {
      const data = {
        name: name,
      }

      const config = {
        headers: {
          'Content-Type': 'application/json'
        }
      }

      axios.post('http://192.168.0.100:5000/api/v1/start', data, config)
          .then(response => {
            console.log(response.data)
          })
          .catch(error => {
            console.error(error)
          })
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