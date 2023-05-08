<template>
  <main>
    <AppRegistration v-if="isVisible" @visible="handleSubmit"/>
    <AppGame v-if="!isVisible"/>
  </main>
</template>

<script>
import AppRegistration from "@/components/AppRegistration.vue";
import AppGame from "@/components/AppGame.vue";

export default {
  name: "PageHome",
  components: {
    AppGame,
    AppRegistration,

  },
  data() {
    return {
      isVisible: true,
    };
  },
  methods: {
    handleSubmit(results) {
      console.log(results);
      this.isVisible = false;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background-color: #1d1e21;
  font-family: 'Roboto', Arial, sans-serif;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
main {
  height: calc(100vh - 68px - 68px);
  padding: 20px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: #fff;
}
</style>