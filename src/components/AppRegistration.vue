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

export default {
  name: "AppRegistration",
  components: { AppInput, AppButton },
  methods: {
    submitData() {
      this.$emit("visible", {
        data: false,
        inputValue: this.$refs.input.inputValue,
      });
    },
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