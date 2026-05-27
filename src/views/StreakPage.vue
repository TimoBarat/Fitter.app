<template>
  <div class="page">

    <!-- HEADER -->
    <header class="topbar">

      <button class="back" @click="goHome">
        ←
      </button>

      <h1>Streak</h1>

    </header>

    <!-- HERO CARD -->
    <section class="hero">

      <div class="hero-left">
        <div class="big-number">
          {{ streak }}
        </div>
        <div class="subtext">
          Current Streak
        </div>
      </div>

      <div class="hero-right">
        🔥
      </div>

    </section>

    <!-- TITLE -->
    <h2 class="title">Calendar</h2>

    <!-- CALENDAR -->
    <main class="calendar">

      <div
        class="month"
        v-for="(month, mIndex) in months"
        :key="mIndex"
      >

        <!-- MONTH HEADER -->
        <div class="month-title">
          {{ month.name }}
        </div>

        <!-- WEEK DAYS -->
        <div class="weekdays">
          <div v-for="d in weekDays" :key="d">
            {{ d }}
          </div>
        </div>

        <!-- DAYS GRID -->
        <div class="grid">

          <!-- EMPTY SPACES -->
          <div
            v-for="n in month.offset"
            :key="'empty' + n"
            class="empty"
          ></div>

          <!-- DAYS -->
          <div
            v-for="day in month.days"
            :key="day.date"
            class="day"
            :class="day.state"
          >
            <span v-if="day.state !== 'STREAK_COMPLETED'">
              {{ day.date }}
            </span>

            <span v-else class="flame">🔥</span>
          </div>

        </div>

      </div>

    </main>

  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const streak = ref(74)

function goHome() {
  router.push('/home')
}

const weekDays = ['Mon','Tue','Wed','Thu','Fri','Sat','Sun']

/*
STATE:
DEFAULT
STREAK_COMPLETED
TARGET_HIGHLIGHT
*/

const months = ref([
  {
    name: 'January 2026',
    offset: 3,
    days: generateMonth(31, 'streak')
  },
  {
    name: 'February 2026',
    offset: 6,
    days: generateMonth(28, 'mixed')
  }
])

function generateMonth(daysCount, type) {
  const arr = []

  for (let i = 1; i <= daysCount; i++) {

    let state = 'DEFAULT'

    if (type === 'streak' && i < 25) {
      state = 'STREAK_COMPLETED'
    }

    if (type === 'mixed' && i === 17) {
      state = 'TARGET_HIGHLIGHT'
    }

    arr.push({
      date: i,
      state
    })
  }

  return arr
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.page {
  min-height: 100vh;
  background: #1a1a1a;
  color: white;
  font-family: 'Segoe UI', sans-serif;
  padding-bottom: 40px;
}

/* TOPBAR */
.topbar {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 18px;
}

.back {
  background: none;
  border: none;
  color: #aaa;
  font-size: 28px;
  cursor: pointer;
}

.topbar h1 {
  font-family: Georgia, serif;
  color: #e74c3c;
}

/* HERO */
.hero {
  background: #2b2b2b;
  margin: 0 16px;
  padding: 20px;
  border-radius: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #e74c3c;
}

.big-number {
  font-size: 48px;
  font-weight: 800;
  color: #e74c3c;
}

.subtext {
  opacity: 0.7;
}

.hero-right {
  font-size: 40px;
}

/* TITLE */
.title {
  margin: 20px 16px 10px;
  color: #e74c3c;
  font-family: Georgia, serif;
}

/* CALENDAR */
.calendar {
  padding: 0 16px;
  display: flex;
  flex-direction: column;
  gap: 18px;
}

/* MONTH */
.month {
  background: #2a2a2a;
  border: 1px solid #e74c3c;
  border-radius: 18px;
  padding: 12px;
}

/* MONTH TITLE */
.month-title {
  text-align: center;
  margin-bottom: 10px;
  color: #ffb347;
  font-weight: 600;
}

/* WEEKDAYS */
.weekdays {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  font-size: 12px;
  color: #aaa;
  text-align: center;
  margin-bottom: 6px;
}

/* GRID */
.grid {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 6px;
}

/* EMPTY */
.empty {
  height: 34px;
}

/* DAY */
.day {
  height: 34px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;
  border: 1px solid #555;
  color: #ddd;
}

/* STREAK (orange flame) */
.STREAK_COMPLETED {
  background: #ff8c00;
  color: black;
  border: none;
}

/* HIGHLIGHT (red special day) */
.TARGET_HIGHLIGHT {
  background: #e74c3c;
  color: white;
  border: none;
}

.flame {
  font-size: 14px;
}
</style>