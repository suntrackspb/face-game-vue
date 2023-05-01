<template>
  <a :href="path" class="menu-item">{{ label }}</a>
</template>

<script>
export default {
  name: "MenuItem",
  props: {
    path: {
      type: String,
      required: true,
    },
    label: {
      type: String,
      required: true,
    },
  },
};
</script>

<style scoped>
  .menu-item {
    padding: 5px 15px;
  }
</style>