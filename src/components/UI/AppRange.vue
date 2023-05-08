<template>

    <input
        type="range"
        min="5"
        step="5"
        :max="maxValue"
        v-model="rangeValue">
    <p>Количество вопросов: {{ rangeValue }}</p>

</template>

<script>
export default {
  name: "AppRange",
  data() {
    return {
      rangeValue: 5
    }
  },
  props: {
    maxValue: {
      type: Number,
      required: true
    },
  },
  watch: {
    maxValue(newValue) {
      if (newValue < this.rangeValue) {
        this.rangeValue = newValue;
      }
    }
  }
};
</script>

<style>
input[type="range"]{
  -webkit-appearance:none;
  width:100%;
  height:20px;
  margin:10px 50px;
  background: linear-gradient(to right, #8438b0 0%, #8438b0 100%);
  background-size:100% 10px;
  background-position:center;
  background-repeat:no-repeat;
  overflow:hidden;
  outline: none;
}

input[type="range"]:first-of-type{
  margin-top:30px;
}

input[type="range"]::-webkit-slider-thumb{
  -webkit-appearance:none;
  width:20px;
  height:20px;
  background: #ffffff;
  position:relative;
  z-index:3;
  box-shadow:0 0 5px 0 rgba(0,0,0,0.3);
}

input[type="range"]::-webkit-slider-thumb:after{
  content:" ";
  width:160px;
  height:10px;
  position:absolute;
  z-index:1;
  right:20px;
  top:5px;
  background: #8438b0;
  background: linear-gradient(to right, #f088fc 1%, #AC6CFF 70%);
}
</style>