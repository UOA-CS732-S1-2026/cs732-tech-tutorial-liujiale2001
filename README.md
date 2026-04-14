# Vue Travel Planner (CS732 Tech Tutorial)

## Introduction

This project is a simple travel planner built using Vue 3.

It was created as part of the CS732 Tech Tutorial assignment to demonstrate core Vue concepts such as components, reactive data, and user interaction.

---

## Features

- Display a list of travel activities
- Add activities to a selected list
- Remove activities from the list
- Prevent duplicate selections
- Automatically calculate total price
- Basic navigation using Vue Router (Home & About page)

---

## Technologies Used

- Vue 3
- Vite
- JavaScript (ES6)
- CSS
- Vue Router

---

## Project Structure

src/
├── components/
│   └── ActivityCard.vue
├── data/
│   └── activities.js
├── pages/
│   ├── Home.vue
│   └── About.vue
├── router/
│   └── index.js
├── App.vue
├── main.js

---

## How to Run the Project

1. Clone the repository

git clone <your-repo-link>

2. Navigate into the project folder

cd cs732-vue-tutorial

3. Install dependencies

npm install

4. Start the development server

npm run dev

5. Open in browser:

http://localhost:5173/

---

## Key Vue Concepts Demonstrated

### Components
The application is built using reusable components such as ActivityCard.

### Props
Data is passed from parent to child components using props.

### Event Handling
Child components emit events to communicate with the parent.

Example:
$emit('add', activity)

### Reactive Data
Selected activities are stored in a reactive array.

### Computed Properties
The total price is automatically calculated based on selected items.

### Vue Router
Basic navigation between Home and About pages is implemented.

---

## Comparison with React

Vue uses templates instead of JSX and has built-in reactivity, which makes it easier to get started.

React provides more flexibility and has a larger ecosystem.

---

## Conclusion

This project demonstrates how Vue can be used to build interactive user interfaces and helped me understand the differences between Vue and React.
