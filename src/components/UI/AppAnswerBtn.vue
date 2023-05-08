<template>
  <button class="app-ans-button"><slot/></button>
</template>

<script>
export default {
  name: "AppAnswerBtn"
}
</script>

<style scoped>
.app-ans-button {
  padding: 10px;
  border: none;
  background: #7a7a7a;
  color: white;
  width: 50%;
  box-sizing: border-box;
  text-align: center;
}
.app-ans-button:hover {
  background: green;
  color: white;

}
.app-ans-button:nth-child(1) {
  border-right: 2px solid #333;
  border-bottom: 2px solid #333;
  border-radius: 0;
}
.app-ans-button:nth-child(2) {
  border-left: 2px solid #333;
  border-right: none;
  border-bottom: 2px solid #333;
  border-radius: 0;
}
.app-ans-button:nth-child(3) {
  border-top: 2px solid #333;
  border-right: 2px solid #333;
  border-bottom: none;
  border-left: none;
  border-radius: 0 0 0 10px;
}
.app-ans-button:nth-child(4) {
  border-top: 2px solid #333;
  border-left: 2px solid #333;
  border-bottom: none;
  border-radius: 0 0 10px 0;
}
@media(max-width: 450px) {
  .app-ans-button {
    width: 100%;
    margin-bottom: 5px;
    font-size: 15px;
  }
  .app-ans-button:nth-child(1) {
    border-radius: 0;
    border: none;
  }
  .app-ans-button:nth-child(2) {
    border-radius: 0;
    border: none;
  }
  .app-ans-button:nth-child(3) {
    border-radius: 0;
    border: none;
  }
  .app-ans-button:nth-child(4) {
    border-radius: 0 0 10px 10px;
    border: none;
  }
  .app-ans-button:hover {
    background: #7a7a7a;
    color: white;
  }
  .app-ans-button:active {
    background: #89d23b;
    color: white;
    transition: all 0.1s ease;
  }
}
</style>