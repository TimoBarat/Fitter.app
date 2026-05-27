<template>
  <div class="page">

    <!-- TOP BAR -->
    <header class="topbar">

      <button class="back" @click="goBack">
        ←
      </button>

      <h1>Add Meal</h1>

      <div></div>
    </header>

    <!-- SEARCH BAR -->
    <div class="search-bar">

      <div class="search-input">
        🔍
        <input
          type="text"
          placeholder="Search Food"
          v-model="search"
        />
      </div>

      <button class="add-btn">
        +
      </button>

    </div>

    <!-- CONTENT -->
    <main class="content">

      <!-- FAVORITES -->
      <section class="section">

        <h2 class="section-title">Favourite</h2>

        <FoodRow
          v-for="(food, i) in favorites"
          :key="i"
          :food="food"
          favorite
        />

      </section>

      <!-- RECENT -->
      <section class="section">

        <h2 class="section-title">Recent</h2>

        <FoodRow
          v-for="(food, i) in recent"
          :key="i"
          :food="food"
        />

      </section>

      <!-- ALL -->
      <section class="section">

        <h2 class="section-title">All</h2>

        <FoodRow
          v-for="(food, i) in filteredFoods"
          :key="i"
          :food="food"
        />

      </section>

    </main>

  </div>
</template>

<script setup>
import { ref, computed } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

/* BACK */
function goBack() {
  router.push('/nutrition')
}

/* SEARCH */
const search = ref('')

/* DATA */
const favorites = ref([
  { name: 'Banana', cals: 122 }
])

const recent = ref([
  { name: 'Banana', cals: 122 },
  { name: 'Apple', cals: 95 }
])

const foods = ref([
  { name: 'Banana', cals: 122 },
  { name: 'Apple', cals: 95 },
  { name: 'Rice', cals: 200 },
  { name: 'Chicken Breast', cals: 165 },
  { name: 'Eggs', cals: 70 }
])

const filteredFoods = computed(() => {
  if (!search.value) return foods.value

  return foods.value.filter(f =>
    f.name.toLowerCase().includes(search.value.toLowerCase())
  )
})

/* FOOD ROW COMPONENT */
const FoodRow = {
  props: ['food', 'favorite'],
  template: `
    <div class="food-row">

      <div class="left">

        <span v-if="favorite" class="star">★</span>

        <div>
          <div class="name">{{ food.name }}</div>
          <div class="cal">{{ food.cals }} cals per 1 serving</div>
        </div>

      </div>

      <div class="arrow">›</div>

    </div>
  `
}
</script>

<style scoped>
.page {
  min-height: 100vh;
  background: #1a1a1a;
  color: white;
  font-family: 'Segoe UI', sans-serif;
  display: flex;
  flex-direction: column;
}

/* TOP */
.topbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px;
  background: #1a1a1a;
}

.topbar h1 {
  font-size: 20px;
  color: #aaa;
}

.back {
  background: none;
  border: none;
  color: #aaa;
  font-size: 26px;
  cursor: pointer;
}

/* SEARCH */
.search-bar {
  display: flex;
  gap: 10px;
  padding: 0 16px 16px;
}

.search-input {
  flex: 1;
  background: #2a2a2a;
  border-radius: 999px;
  padding: 10px 14px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.search-input input {
  flex: 1;
  background: none;
  border: none;
  outline: none;
  color: white;
}

.add-btn {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  border: none;
  background: #444;
  color: white;
  font-size: 22px;
  cursor: pointer;
}

/* CONTENT */
.content {
  flex: 1;
  overflow-y: auto;
  padding: 10px 16px 120px;
}

/* SECTION */
.section {
  margin-bottom: 24px;
}

.section-title {
  color: #e74c3c;
  font-family: Georgia, serif;
  font-size: 20px;
  margin-bottom: 10px;
}

/* FOOD ROW */
.food-row {
  background: #2a2a2a;
  padding: 14px;
  border-radius: 14px;
  margin-bottom: 10px;

  display: flex;
  justify-content: space-between;
  align-items: center;

  cursor: pointer;
}

.left {
  display: flex;
  gap: 10px;
  align-items: center;
}

.star {
  color: gold;
  font-size: 18px;
}

.name {
  font-weight: 600;
}

.cal {
  font-size: 12px;
  color: #aaa;
}

.arrow {
  color: #aaa;
  font-size: 20px;
}
</style>