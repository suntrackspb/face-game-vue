<template>
  <button class="btn"><slot/></button>
</template>

<script>
export default {
  name: "AppButton"
}
</script>

<style scoped>
  .btn {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    font-weight: bold;
    font-size: 20px;
    padding: 15px 30px;
    color: white;
    background: darkviolet;
    border: 1px solid darkviolet;
    border-radius: 5px;
    width: 100%;
  }
  .btn:hover {
    color: darkviolet;
    background: white;
    border: 1px solid darkviolet;
  }
</style>