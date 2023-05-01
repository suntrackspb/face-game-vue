<template>
  <nav class="app-navbar">
    <div class="app-navbar__logo">
      <a href="/">FaceGame</a>
    </div>
    <ul class="app-navbar__menu">
      <li v-for="item in menuItems" :key="item.label">
        <MenuItem :path="item.path" :label="item.label"></MenuItem>
      </li>
    </ul>
  </nav>
</template>


<script>
import MenuItem from "@/components/UI/MenuItem.vue";

export default {
  name: "AppNavbar",
  components: { MenuItem },
  data() {
    return {
      menuItems: [
        { path: "/", label: "Home" },
        { path: "/about", label: "About" },
        { path: "/contact", label: "Contact" },
      ],
    };
  },
};
</script>


<style>
.app-navbar {
  background-color: #333;
  color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 150px;
  border-radius: 10px;
}

.app-navbar__logo {
  font-size: 24px;
}

.app-navbar__logo a {
  color: #fff;
  text-decoration: none;
}

.app-navbar__menu {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

.app-navbar__menu li + li {
  margin-left: 10px;
}

.app-navbar__menu li a {
  color: #fff;
  text-decoration: none;
}

.app-navbar__menu li a:hover {
  text-decoration: underline;
  color: aqua;
}
</style>