<template>
<div class="app__not-found">
  <h2>Page not found</h2>
  <h1>404</h1>
</div>
</template>

<script>
export default {
  name: "NotFound"
}
</script>

<style scoped>
.app__not-found {
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: calc(100vh - 68px);
  color: #d05d2e;
}
</style>