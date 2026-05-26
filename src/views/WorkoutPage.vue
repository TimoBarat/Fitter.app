<template>
  <div class="page">

    <!-- TOP HEADER -->
    <header class="topbar">
      <div class="profile-section">
        <img
          class="avatar"
          src="https://i.pravatar.cc/100"
          alt="Profile"
        />

        <div class="streak">
          <span>74</span>
          <span class="fire">🔥</span>
        </div>
      </div>
    </header>

    <!-- MAIN CONTENT -->
    <main class="content">

      <!-- ROUTINES -->
      <section class="section">

        <div class="section-header">
          <h1>My Workout Routines</h1>
          <span class="search-icon">⌕</span>
        </div>

        <!-- START EMPTY -->
        <button
          class="main-btn"
          @click="startEmptyWorkout"
        >
          Start Empty
        </button>

        <button class="main-btn">
          Generate Workout
        </button>

      </section>

      <!-- PAST WORKOUTS -->
      <section class="section">

        <h1>Past Workouts</h1>

        <div class="workout-card">

          <div class="card-header">
            <h2>Lower Body Routine</h2>
            <span class="menu">⋮</span>
          </div>

          <p class="subtitle">
            4 sets • 6 exercises
          </p>

          <div class="exercise-list">
            <div class="exercise-pill">
              Squat
            </div>

            <div class="exercise-pill">
              Leg Press
            </div>

            <div class="exercise-pill">
              Lunges
            </div>
          </div>

          <div class="card-footer">

            <span class="more-text">
              show 3 more exercises...
            </span>

            <button
              class="start-btn"
              @click="startWorkout"
            >
              START
            </button>

          </div>

        </div>

      </section>

    </main>

    <!-- BOTTOM NAV -->
    <nav class="bottom-nav">
      <div class="nav-item active">🏋</div>
      <div class="nav-item" @click="goHome"> ⌂ </div>
      <div class="nav-item">🍴</div>
      <div class="nav-item">👤</div>
    </nav>

  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

// START EMPTY
function startEmptyWorkout() {
  router.push({
    name: 'StartWorkout',
    query: {
      empty: 'true'
    }
  })
}

// NORMAL WORKOUT
function startWorkout() {
  router.push({
    name: 'StartWorkout'
  })
}

function goHome() {
  router.push({
    name: 'Homepage'
  })
}
</script>

<style scoped>
.page {
  width: 100%;
  min-height: 100vh;
  background: #d7b2b2;
  display: flex;
  flex-direction: column;
}

.topbar {
  background: #5b1f1f;
  padding: 18px 20px;
  border-bottom-left-radius: 24px;
  border-bottom-right-radius: 24px;
}

.profile-section {
  display: flex;
  align-items: center;
  gap: 14px;
}

.avatar {
  width: 54px;
  height: 54px;
  border-radius: 50%;
}

.streak {
  display: flex;
  align-items: center;
  gap: 6px;
  color: white;
  font-size: 24px;
  font-weight: 700;
}

.content {
  flex: 1;
  overflow-y: auto;
  padding: 24px 20px 120px;
}

.section {
  margin-bottom: 34px;
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.section h1 {
  color: #5b1f1f;
  font-size: 32px;
  margin-bottom: 18px;
  font-family: Georgia, serif;
}

.search-icon {
  font-size: 28px;
  color: #5b1f1f;
}

.main-btn {
  width: 100%;
  border: none;
  background: #5b1f1f;
  color: #f0dada;
  padding: 18px;
  border-radius: 999px;
  margin-bottom: 16px;
  font-size: 18px;
  font-weight: 600;
}

.workout-card {
  background: #6e2a2a;
  border-radius: 28px;
  padding: 20px;
  margin-bottom: 24px;
  color: #f5dede;
}

.card-header {
  display: flex;
  justify-content: space-between;
}

.subtitle {
  margin-top: 8px;
  margin-bottom: 18px;
}

.exercise-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.exercise-pill {
  background: #4f1b1b;
  padding: 14px 18px;
  border-radius: 999px;
}

.card-footer {
  margin-top: 18px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.start-btn {
  border: none;
  background: #2d0d0d;
  color: white;
  width: 76px;
  height: 76px;
  border-radius: 50%;
}

.bottom-nav {
  position: fixed;
  bottom: 0;
  width: 100%;
  background: #5b1f1f;
  display: flex;
  justify-content: space-around;
  padding: 16px 0;
}

.nav-item {
  color: #f1dede;
  font-size: 28px;
}
</style>