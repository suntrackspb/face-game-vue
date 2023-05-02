<template>
  <select class="app-select" v-model="selectValue">
    <option
        v-for="cat in categories"
        :key="cat.id"
    > {{cat.name}}</option>
  </select>
</template>

<script>

export default {
  name: "AppSelector",
  data() {
    return {
      categories: [
        {id: "1", name: "Актёры"},
        {id: "2", name: "Политики"},
        {id: "3", name: "Музыканты"},
        {id: "4", name: "Долбаёбы"},
      ],
      selectValue: 'Актёры'
    }
  },
}
</script>

<style scoped>
.app-select {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: 20px;
  padding: 15px;
  color: white;
  background-color: darkviolet;
  border: 1px solid darkviolet;
  border-radius: 5px;
  width: 100%;
  text-align: center;
}
select {
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  background-image: url('../../../public/images/arrow.png');
  background-size: 20px;
  background-repeat: no-repeat;
  background-position-y: center;
  background-position-x: calc(100% - 20px);
  padding-right: 20px;
  border: 1px solid #ccc;
}
</style>