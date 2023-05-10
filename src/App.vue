<template>
  <div id="container">
    <nav class="navbar">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item">My App</router-link>
      </div>
  <div class="navbar-menu" :class="{ 'is-active': isMenuOpen }">
    <div class="navbar-end">
      <router-link to="/task" class="navbar-item">Tasks</router-link>
    </div>
  </div>
</nav>

<router-view></router-view>
  </div>
</template>
<script>
export default {
  name: 'App',
  data() {
    return {
      isMenuOpen: false
    }
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen
    }
  }
}
</script>
<style>
.navbar {
  background-color: #06283D;
  color: white;
}

.navbar-burger {
  background-color: transparent;
  border: none;
  margin-right: 1rem;
}

.navbar-burger span {
  display: block;
  width: 25px;
  height: 3px;
  background-color: white;
  margin-bottom: 5px;
}

.navbar-menu {
  background-color: #06283D;
}

.navbar-item {
  color: white;
  font-weight: bold;
}

.navbar-item:hover {
  color: #00d1b2;
}
</style>