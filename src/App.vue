<template>
  <div>
    <header class="navbar">
      <div class="logo">Travel Planner</div>
      <nav class="nav-links">
        <router-link to="/">Home</router-link>
        <router-link to="/about">About</router-link>
      </nav>
    </header>

    <router-view />
  </div>
</template>

<script>
export default {
  name: "App"
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f7f9fb;
  color: #1f2937;
}

a {
  text-decoration: none;
  color: inherit;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 40px;
  background: #0b2727;
  color: white;
}

.logo {
  font-size: 24px;
  font-weight: bold;
}

.nav-links {
  display: flex;
  gap: 24px;
}

.nav-links a {
  color: white;
  font-size: 16px;
}

.nav-links a.router-link-active {
  color: #ffb266;
  font-weight: bold;
}

@media (max-width: 900px) {
  .navbar {
    flex-direction: column;
    gap: 12px;
    text-align: center;
  }
}
</style>