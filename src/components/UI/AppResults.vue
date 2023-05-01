<template>
<div>
  <h1>END</h1>
  <div v-for="i in res" :key="i">
    <span :class="i ? 'green' : 'red'">{{ i ? 'Верно' : 'Неверно' }}</span>
  </div>
</div>
</template>

<script>
export default {
  name: "AppResults",
  props: {
    res: Array,
  }
}
</script>

<style scoped>
.green {
  color: green;
}

.red {
  color: red;
}
</style>