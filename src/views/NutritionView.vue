<template>
  <div class="page">

    <!-- TOP HEADER -->
    <header class="topbar">

      <div class="left">
        <img class="avatar" src="https://i.pravatar.cc/100" />

        <div class="streak">
          74 🔥
        </div>
      </div>

      <button class="settings">
        ⚙
      </button>

    </header>

    <!-- MAIN -->
    <main class="content">

      <!-- DASHBOARD -->
      <section class="card">

        <!-- DATE SWITCH -->
        <div class="date-switch">
          <button @click="prevDay">&lt;</button>
          <div class="date-text">{{ currentDate }}</div>
          <button @click="nextDay">&gt;</button>
        </div>

        <!-- MAIN INFO -->
        <div class="dashboard">

          <!-- LEFT: CIRCLE -->
          <div class="circle">
            <div class="kcal">
              {{ kcal }} kcal
            </div>
          </div>

          <!-- RIGHT INFO -->
          <div class="info">
            <p>goal: 2000 kcal</p>
            <p>gained: 1800 kcal</p>
            <p>burn: 1300 kcal</p>

            <div class="small">
              <span>2 meals</span>
              <span>1 exercise</span>
            </div>
          </div>

        </div>

        <!-- MACROS -->
        <div class="macros">

          <div class="macro">
            <div class="dot blue"></div>
            <p>Protein</p>
            <span>0g</span>
          </div>

          <div class="macro">
            <div class="dot green"></div>
            <p>Carbs</p>
            <span>0g</span>
          </div>

          <div class="macro">
            <div class="dot yellow"></div>
            <p>Fat</p>
            <span>0g</span>
          </div>

        </div>

      </section>

      <!-- MEALS -->
      <section class="meals">

        <div
          class="meal"
          v-for="meal in meals"
          :key="meal.name"
        >

          <div class="meal-header">
            <h3>{{ meal.name }}</h3>
            <button class="plus" @click="addMealItem(meal)">
              +
            </button>
          </div>

          <!-- EMPTY -->
          <div v-if="meal.items.length === 0" class="empty">
            + Add Meal
          </div>

          <!-- ITEMS -->
          <div
            v-for="(item, i) in meal.items"
            :key="i"
            class="food"
          >
            <div>
              <strong>{{ item.name }}</strong>
              <small>{{ item.kcal }} Calories</small>
            </div>

            <button
              class="remove"
              @click="removeMealItem(meal, i)"
            >
              −
            </button>
          </div>

        </div>

      </section>

      <!-- CTA -->
      <section class="cta">

        <h2>Personalise plan</h2>

        <button>
          Start questionnaire
        </button>

      </section>

    </main>

    <!-- BOTTOM NAV -->
    <nav class="bottom">

      <div>🏋</div>
      <div class="active">🍴</div>
      <div>🏠</div>
      <div>👤</div>

    </nav>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const kcal = ref(1200)

const currentDate = ref('Today 24 Mar')

const meals = ref([
  { name: 'Breakfast', items: [] },
  { name: 'Snack', items: [] },
  {
    name: 'Lunch',
    items: [
      { name: 'Banana', kcal: 122 }
    ]
  },
  { name: 'Dinner', items: [] }
])

function addMealItem(meal) {
  meal.items.push({
    name: 'New Food',
    kcal: 100
  })
}

function removeMealItem(meal, index) {
  meal.items.splice(index, 1)
}

function prevDay() {
  console.log('prev day')
}

function nextDay() {
  console.log('next day')
}
</script>

<style scoped>
.page {
  min-height: 100vh;
  background: #0f0f10;
  color: white;
  display: flex;
  flex-direction: column;
}

/* TOP BAR */
.topbar {
  display: flex;
  justify-content: space-between;
  padding: 16px;
  background: #1a0f10;
}

.left {
  display: flex;
  align-items: center;
  gap: 10px;
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}

.streak {
  font-weight: bold;
}

.settings {
  background: none;
  border: none;
  color: white;
  font-size: 22px;
}

/* CONTENT */
.content {
  flex: 1;
  overflow-y: auto;
  padding: 16px;
}

/* CARD */
.card {
  background: #2a2a2a;
  border-radius: 18px;
  padding: 16px;
  margin-bottom: 16px;
}

/* DATE */
.date-switch {
  display: flex;
  justify-content: space-between;
  margin-bottom: 12px;
}

.date-text {
  font-weight: bold;
}

/* DASHBOARD */
.dashboard {
  display: flex;
  gap: 16px;
}

.circle {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  border: 6px solid white;
  display: flex;
  align-items: center;
  justify-content: center;
}

.kcal {
  font-weight: bold;
}

.info p {
  margin: 4px 0;
  font-size: 13px;
}

.small {
  margin-top: 8px;
  font-size: 12px;
  opacity: 0.7;
  display: flex;
  gap: 10px;
}

/* MACROS */
.macros {
  display: flex;
  justify-content: space-between;
  margin-top: 16px;
}

.macro {
  text-align: center;
}

.dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  margin: auto;
}

.blue { background: blue; }
.green { background: green; }
.yellow { background: gold; }

/* MEALS */
.meals {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.meal {
  background: #5b1f1f;
  border-radius: 16px;
  padding: 12px;
}

.meal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.plus {
  background: none;
  border: none;
  color: red;
  font-size: 22px;
}

/* EMPTY */
.empty {
  margin-top: 10px;
  padding: 10px;
  background: #3a0f12;
  border-radius: 10px;
  text-align: center;
}

/* FOOD ITEM */
.food {
  display: flex;
  justify-content: space-between;
  background: #f3b5b5;
  color: black;
  padding: 10px;
  border-radius: 10px;
  margin-top: 8px;
}

.food small {
  display: block;
  font-size: 11px;
}

.remove {
  background: none;
  border: none;
  font-size: 22px;
  color: red;
}

/* CTA */
.cta {
  margin-top: 20px;
  text-align: center;
}

.cta button {
  margin-top: 10px;
  padding: 12px;
  border-radius: 999px;
  border: none;
  background: #aaa;
  color: black;
  width: 100%;
  font-weight: bold;
}

/* BOTTOM NAV */
.bottom {
  display: flex;
  justify-content: space-around;
  padding: 12px;
  background: #1a0f10;
}

.bottom .active {
  color: red;
}
</style>