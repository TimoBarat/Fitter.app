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
      <!-- WORKOUT ROUTINES -->
      <section class="section">
        <div class="section-header">
          <h1>My Workout Routines</h1>
          <span class="search-icon">⌕</span>
        </div>

        <button class="main-btn">Start Empty</button>
        <button class="main-btn">Generate Workout</button>
      </section>

      <!-- PAST WORKOUTS -->
      <section class="section">
        <h1>Past Workouts</h1>

        <!-- CARD -->
        <div class="workout-card">
          <div class="card-header">
            <h2>Lower Body Routine</h2>
            <span class="menu">⋮</span>
          </div>

          <p class="subtitle">4 sets • 6 exercises</p>

          <div class="exercise-list">
            <div class="exercise-pill">Exercise 1</div>
            <div class="exercise-pill">Exercise 2</div>
            <div class="exercise-pill">Exercise 3</div>
          </div>

          <div class="card-footer">
            <span class="more-text">
              show 3 more exercises...
            </span>

            <button class="start-btn">
              START
            </button>
          </div>
        </div>

        <!-- SECOND CARD -->
        <div class="workout-card">
          <div class="card-header">
            <h2>Upper Body Routine</h2>
            <span class="menu">⋮</span>
          </div>

          <p class="subtitle">5 sets • 7 exercises</p>

          <div class="exercise-list">
            <div class="exercise-pill">Exercise 1</div>
            <div class="exercise-pill">Exercise 2</div>
            <div class="exercise-pill">Exercise 3</div>
          </div>

          <div class="card-footer">
            <span class="more-text">
              show 4 more exercises...
            </span>

            <button class="start-btn">
              START
            </button>
          </div>
        </div>
      </section>
    </main>

    <!-- BOTTOM NAVBAR -->
    <nav class="bottom-nav">
      <div class="nav-item active">🏋</div>
      <div class="nav-item">⌂</div>
      <div class="nav-item">🍴</div>
      <div class="nav-item">👤</div>
    </nav>
  </div>
</template>

<script setup>
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body,
html,
html,
body,
#app {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
}

/* PAGE */
.page {
  min-height: 100vh;
  background: #d7b2b2;
  display: flex;
  flex-direction: column;
  overflow: hidden;
  width: 100%;
  min-height: 100vh;
  padding: 0;
}


/* TOPBAR */
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
  object-fit: cover;
  border: 2px solid white;
}

.streak {
  display: flex;
  align-items: center;
  gap: 6px;
  color: white;
  font-size: 24px;
  font-weight: 700;
}

.fire {
  font-size: 26px;
}

/* MAIN CONTENT */
.content {
  flex: 1;
  overflow-y: auto;
  padding: 24px 20px 120px;
}

/* SECTION */
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
  cursor: pointer;
}

/* BUTTONS */
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
  cursor: pointer;
  transition: 0.2s ease;
}

.main-btn:hover {
  transform: scale(1.02);
}

/* WORKOUT CARD */
.workout-card {
  background: #6e2a2a;
  border-radius: 28px;
  padding: 20px;
  margin-bottom: 24px;
  color: #f5dede;
  box-shadow: 0 8px 18px rgba(0, 0, 0, 0.18);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card-header h2 {
  margin: 0;
  font-size: 22px;
  font-family: Georgia, serif;
}

.menu {
  font-size: 24px;
  cursor: pointer;
}

.subtitle {
  margin-top: 8px;
  margin-bottom: 18px;
  opacity: 0.85;
  font-size: 14px;
}

/* EXERCISES */
.exercise-list {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.exercise-pill {
  background: #4f1b1b;
  padding: 14px 18px;
  border-radius: 999px;
  font-size: 15px;
}

/* FOOTER */
.card-footer {
  margin-top: 18px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.more-text {
  font-size: 13px;
  opacity: 0.8;
}

.start-btn {
  border: none;
  background: #2d0d0d;
  color: white;
  width: 76px;
  height: 76px;
  border-radius: 50%;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: 0.2s ease;
}

.start-btn:hover {
  transform: scale(1.05);
}

/* BOTTOM NAV */
.bottom-nav {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  background: #5b1f1f;
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 16px 0;
  border-top-left-radius: 22px;
  border-top-right-radius: 22px;
}

.nav-item {
  color: #f1dede;
  font-size: 28px;
  cursor: pointer;
  transition: 0.2s ease;
}

.nav-item.active {
  transform: scale(1.15);
}

.nav-item:hover {
  transform: scale(1.12);
}
</style>