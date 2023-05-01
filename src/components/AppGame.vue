<template>
<div>
  <h1>{{ submittedName }}</h1>
  <h1>Game is ready!</h1>
  <AppGameCard/>
</div>
</template>

<script>
import AppGameCard from "@/components/UI/AppGameCard.vue";

export default {
  name: "AppGame",
  components: {AppGameCard},
  props: {
    submittedName: String,
  },
}
</script>

<style scoped>

</style>