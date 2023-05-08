<script>
import PageLeader from "@/pages/PageLeader";
import NotFound from '@/pages/NotFound'
import PageHome from "@/pages/PageHome";

import MenuItem from "@/components/UI/MenuItem.vue";

const routes = {
  '/': PageHome,
  '/leader': PageLeader
}

export default {
  components: { MenuItem },
  data() {
    return {
      currentPath: window.location.hash,
      menuItems: [
        { path: "#/", label: "Игра" },
        { path: "#/leader", label: "Лидеры" },
      ],
    }
  },
  computed: {
    currentView() {
      return routes[this.currentPath.slice(1) || '/'] || NotFound
    }
  },
  mounted() {
    window.addEventListener('hashchange', () => {
      this.currentPath = window.location.hash
    })
  }
}
</script>

<template>
  <nav class="app-navbar">
    <div class="app-navbar__logo">
      <a href="/"><img class="app_logo" src="./assets/logo2.png"></a>
    </div>
    <ul class="app-navbar__menu">
      <li v-for="item in menuItems" :key="item.label">
        <MenuItem :path="item.path" :label="item.label"></MenuItem>
      </li>
    </ul>
  </nav>
  <component :is="currentView" />
</template>

<style>
.app_logo{
  width: 60px;

}
.app-navbar {
  background-color: #333;
  color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 20px;
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
@media(max-width: 600px) {
  .app-navbar {
    padding: 10px;
  }
}

</style>
