<template>
  <header>
    <AppNavbar />
  </header>

  <main>
    <AppRegistration v-if="isVisible" @visible="handleSubmit"/>
    <AppGame v-if="!isVisible" :submitted-name="submittedName" />
  </main>

  <footer>
    <AppFooter />
  </footer>
</template>

<script>
import AppNavbar from "@/components/AppNavbar.vue";
import AppRegistration from "@/components/AppRegistration.vue";
import AppFooter from "@/components/AppFooter.vue";
import AppGame from "@/components/AppGame.vue";

export default {
  name: "PageComponent",
  components: {
    AppGame,
    AppFooter,
    AppRegistration,
    AppNavbar

  },
  data() {
    return {
      isVisible: true,
      submittedName: "",
      loadedData: "",
    };
  },
  methods: {
    handleSubmit(event) {
      console.log(event);
      this.isVisible = event.data;
      this.submittedName = event.inputValue;
      localStorage.name = this.submittedName;
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
