<template>
  <input
      type="text"
      class="app-input"
      v-model="inputValue"
      :aria-placeholder="ariaPlaceholder"
      :placeholder="placeholder"
  />
</template>

<script>
export default {
  name: "AppInput",
  data() {
    return {
      inputValue: "",
    };
  },
  props: {
    ariaPlaceholder: String,
    placeholder: String,
  },
  mounted() {
    if (localStorage.name){
      this.inputValue = localStorage.name
    }
  }
};
</script>

<style scoped>
 .app-input {
   font-family: Avenir, Helvetica, Arial, sans-serif;
   font-size: 20px;
   padding: 15px;
   color: white;
   background: darkviolet;
   border: 1px solid darkviolet;
   border-radius: 5px;
   width: 100%;
   text-align: center;
 }
 input::placeholder {
   color: #ffffff;
 }
</style>