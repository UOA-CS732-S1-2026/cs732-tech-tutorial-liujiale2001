<template>
  <div class="card">
    <img :src="activity.image" :alt="activity.title" class="card-image" />
    <div class="card-body">
      <h3>{{ activity.title }}</h3>
      <p class="location">{{ activity.location }}</p>
      <div class="card-footer">
        <span class="price">${{ activity.price }}</span>
        <button @click="$emit('add', activity)">Add</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ActivityCard",
  props: {
    activity: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.card {
  background: white;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.08);
  transition: transform 0.2s ease;
}

.card:hover {
  transform: translateY(-4px);
}

.card-image {
  width: 100%;
  height: 220px;
  object-fit: cover;
}

.card-body {
  padding: 18px;
}

.card-body h3 {
  margin: 0 0 8px;
  font-size: 22px;
  color: #0b2727;
}

.location {
  margin: 0 0 16px;
  color: #6b7280;
}

.card-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.price {
  font-weight: bold;
  color: #ff7e01;
  font-size: 18px;
}

button {
  border: none;
  background: #0b2727;
  color: white;
  padding: 10px 16px;
  border-radius: 10px;
  cursor: pointer;
}

button:hover {
  opacity: 0.9;
}
</style>