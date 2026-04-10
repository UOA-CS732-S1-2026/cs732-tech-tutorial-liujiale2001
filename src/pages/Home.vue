<template>
  <div class="app">
    <section class="hero">
      <div class="hero-content">
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
          @add="addActivity"
        />
      </div>
    </section>

    <section class="selected-section">
      <div class="selected-box">
        <h2>Selected Activities</h2>
        <p class="selected-subtitle">Your chosen experiences will appear here.</p>

        <ul v-if="selectedActivities.length > 0" class="selected-list">
          <li v-for="item in selectedActivities" :key="item.id" class="selected-item">
            <div>
              <strong>{{ item.title }}</strong>
              <p>{{ item.location }}</p>
            </div>

            <div class="selected-actions">
              <span class="selected-price">${{ item.price }}</span>
              <button class="remove-btn" @click="removeActivity(item.id)">Remove</button>
            </div>
          </li>
        </ul>

        <p v-else class="empty-text">No activities selected yet.</p>

        <div v-if="selectedActivities.length > 0" class="total-box">
          Total: ${{ totalPrice }}
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import ActivityCard from "../components/ActivityCard.vue"
import { activities } from "../data/activities.js"

export default {
  name: "Home",
  components: {
    ActivityCard
  },
  data() {
    return {
      activities,
      selectedActivities: []
    }
  },
  methods: {
    addActivity(activity) {
      const exists = this.selectedActivities.some(
        item => item.id === activity.id
      )

      if (!exists) {
        this.selectedActivities.push(activity)
      }
    },
    removeActivity(id) {
      this.selectedActivities = this.selectedActivities.filter(
        item => item.id !== id
      )
    }
  },
  computed: {
    totalPrice() {
      return this.selectedActivities.reduce((sum, item) => {
        return sum + item.price
      }, 0)
    }
  }
}
</script>

<style scoped>
.hero {
  padding: 80px 20px 50px;
  background: linear-gradient(135deg, #eef6f6, #ffffff);
}

.hero-content {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
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

.selected-section {
  padding: 0 40px 80px;
}

.selected-box {
  max-width: 900px;
  margin: 0 auto;
  background: white;
  border-radius: 18px;
  padding: 28px;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
}

.selected-box h2 {
  margin: 0 0 8px;
  color: #0b2727;
  font-size: 30px;
}

.selected-subtitle {
  margin: 0 0 24px;
  color: #6b7280;
}

.selected-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.selected-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 0;
  border-bottom: 1px solid #e5e7eb;
}

.selected-item:last-child {
  border-bottom: none;
}

.selected-item strong {
  display: block;
  font-size: 18px;
  color: #0b2727;
  margin-bottom: 4px;
}

.selected-item p {
  margin: 0;
  color: #6b7280;
}

.selected-price {
  font-weight: bold;
  color: #ff7e01;
  font-size: 18px;
}

.empty-text {
  color: #9ca3af;
  text-align: center;
  padding: 20px 0;
}

.selected-actions {
  display: flex;
  align-items: center;
  gap: 12px;
}

.remove-btn {
  border: none;
  background: #ef4444;
  color: white;
  padding: 8px 14px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 14px;
}

.remove-btn:hover {
  opacity: 0.9;
}

.total-box {
  margin-top: 20px;
  text-align: right;
  font-size: 22px;
  font-weight: bold;
  color: #0b2727;
}

@media (max-width: 900px) {
  .activities-grid {
    grid-template-columns: 1fr;
  }

  .hero h1 {
    font-size: 38px;
  }

  .selected-item {
    flex-direction: column;
    align-items: flex-start;
    gap: 12px;
  }
}
</style>