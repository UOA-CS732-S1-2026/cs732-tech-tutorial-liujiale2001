<template>
  <div class="app">
    <header class="navbar">
      <div class="logo">Vue Travel Planner</div>
      <nav class="nav-links">
        <a href="#">Home</a>
        <a href="#">Activities</a>
        <a href="#">About</a>
      </nav>
    </header>

    <section class="hero">
      <div class="hero-content">
        <p class="hero-tag">CS732 Tech Tutorial Project</p>
        <h1>Explore New Zealand with Vue</h1>
        <p class="hero-text">
          A simple travel planner demo built with Vue to demonstrate components,
          reusable UI, and modern front-end development.
        </p>
      </div>
    </section>

    <section class="activities-section">
      <div class="section-header">
        <h2>Popular Activities</h2>
        <p>Choose from some iconic New Zealand travel experiences.</p>
      </div>

      <div class="activities-grid">
        <ActivityCard
          v-for="activity in activities"
          :key="activity.id"
          :activity="activity"
        />
      </div>
    </section>
  </div>
</template>

<script>
import ActivityCard from "./components/ActivityCard.vue"
import { activities } from "./data/activities.js"

export default {
  name: "App",
  components: {
    ActivityCard
  },
  data() {
    return {
      activities
    }
  }
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

.hero {
  padding: 80px 20px 50px;
  background: linear-gradient(135deg, #eef6f6, #ffffff);
}

.hero-content {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

.hero-tag {
  color: #ff7e01;
  font-weight: bold;
  margin-bottom: 12px;
  letter-spacing: 1px;
}

.hero h1 {
  font-size: 52px;
  margin: 0 0 20px;
  color: #0b2727;
}

.hero-text {
  font-size: 18px;
  line-height: 1.7;
  color: #4b5563;
  margin: 0 auto;
  max-width: 700px;
}

.activities-section {
  padding: 60px 40px 80px;
}

.section-header {
  text-align: center;
  margin-bottom: 32px;
}

.section-header h2 {
  font-size: 36px;
  margin-bottom: 10px;
  color: #0b2727;
}

.section-header p {
  color: #6b7280;
  font-size: 17px;
}

.activities-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  max-width: 1200px;
  margin: 0 auto;
}

@media (max-width: 900px) {
  .activities-grid {
    grid-template-columns: 1fr;
  }

  .hero h1 {
    font-size: 38px;
  }

  .navbar {
    flex-direction: column;
    gap: 12px;
    text-align: center;
  }
}
</style>