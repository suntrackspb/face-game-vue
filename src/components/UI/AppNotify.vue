<template>
  <div class="notification" :class="{ show: show }">
    {{ message }}
  </div>
</template>

<script>
export default {
  name: "AppNotify",
  props: {
    message: String,
    delay: Number // время показа уведомления в ms
  },
  data() {
    return {
      show: true
    }
  },
  mounted() {
    setTimeout(() => {
      this.show = false
    }, this.delay)
  }
}
</script>

<style scoped>
.notification {
  color: red;
  display: none;
  position: fixed;
  top: 50px;
  left: 50%;
  transform: translateX(-50%);
  padding: 10px 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #fff;
  box-shadow: 0 1px 3px rgba(0, 0, 0, .3), 0 1px 2px rgba(0, 0, 0, .1);
}

.notification.show {
  display: block;
  animation: notification 0.3s ease-out forwards;
}

@keyframes notification {
  0% {
    transform: translateX(-50%) translateY(-10px);
    opacity: 0;
  }
  100% {
    transform: translateX(-50%) translateY(0);
    opacity: 1;
  }
}
</style>