<template>
  <button class="app-button"><slot/></button>
</template>

<script>
export default {
  name: "AppAnswerBtn"
}
</script>

<style scoped>
.app-button {
  padding: 10px;
}
</style>