<template>
  <div class="page">

    <!-- TOP BAR -->
    <header class="topbar">
      <button class="back">←</button>
      <h1>Workout</h1>
    </header>

    <!-- SUB HEADER -->
    <div class="subheader">
      <input class="routine-name" v-model="workoutName" />
      <div class="timer">00:00</div>
    </div>

    <!-- CONTENT -->
    <main class="content">

      <!-- EXERCISES -->
      <div
        class="exercise-card"
        v-for="(ex, i) in exercises"
        :key="i"
      >

        <!-- EXERCISE HEADER -->
        <div class="exercise-header">

          <input
            class="exercise-title"
            v-model="ex.name"
          />

          <!-- DELETE EXERCISE -->
          <button
            class="delete-exercise"
            @click="deleteExercise(i)"
          >
            🗑
          </button>

        </div>

        <!-- GRID HEADER -->
        <div class="grid header">
          <div>SET</div>
          <div>PREV</div>
          <div>KG</div>
          <div>REPS</div>
          <div></div>
        </div>

        <!-- SETS -->
        <div
          class="grid row"
          v-for="(set, s) in ex.sets"
          :key="s"
        >
          <div>{{ s + 1 }}</div>

          <div class="locked">{{ set.prev }}</div>

          <input type="number" v-model="set.kg" />
          <input type="number" v-model="set.reps" />

          <div class="actions">
            <button
              class="check"
              :class="{ done: set.done }"
              @click="set.done = !set.done"
            >
              ✓
            </button>

            <button
              class="delete"
              @click="deleteSet(i, s)"
            >
              🗑
            </button>
          </div>
        </div>

        <!-- ADD SET -->
        <button class="add-set" @click="addSet(i)">
          Add set +
        </button>

      </div>

      <!-- ADD EXERCISE -->
      <button class="add-exercise" @click="addExercise">
        Add exercise +
      </button>

    </main>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const workoutName = ref('Lower Body Routine')

const exercises = ref([
  {
    name: 'Squat',
    sets: [
      { prev: '60 × 8', kg: 60, reps: 8, done: false },
      { prev: '60 × 8', kg: 60, reps: 8, done: false }
    ]
  },
  {
    name: 'Lunges',
    sets: [
      { prev: '40 × 10', kg: 40, reps: 10, done: false },
      { prev: '-', kg: 0, reps: 0, done: false }
    ]
  }
])

// ADD SET
function addSet(index) {
  exercises.value[index].sets.push({
    prev: '-',
    kg: 0,
    reps: 0,
    done: false
  })
}

// DELETE SET
function deleteSet(exIndex, setIndex) {
  exercises.value[exIndex].sets.splice(setIndex, 1)
}

// ADD EXERCISE
function addExercise() {
  exercises.value.push({
    name: 'New Exercise',
    sets: [
      { prev: '-', kg: 0, reps: 0, done: false },
      { prev: '-', kg: 0, reps: 0, done: false }
    ]
  })
}

// DELETE EXERCISE
function deleteExercise(index) {
  exercises.value.splice(index, 1)
}
</script>

<style scoped>
.page {
  min-height: 100vh;
  background: #d7b2b2;
  display: flex;
  flex-direction: column;
}

/* TOP BAR */
.topbar {
  background: #5b1f1f;
  padding: 18px;
  display: flex;
  align-items: center;
  gap: 12px;
  color: white;
}

.topbar h1 {
  font-family: Georgia, serif;
  font-size: 22px;
  margin: auto;
}

.back {
  background: none;
  border: none;
  color: white;
  font-size: 26px;
  cursor: pointer;
}

/* SUB HEADER */
.subheader {
  display: flex;
  justify-content: space-between;
  padding: 14px 18px;
  color: #5b1f1f;
  font-weight: 600;
}

.routine-name {
  border: none;
  background: transparent;
  font-size: 18px;
  font-weight: 600;
  color: #5b1f1f;
  outline: none;
}

.timer {
  font-weight: 700;
  font-family: sans-serif;
}

/* CONTENT */
.content {
  flex: 1;
  overflow-y: auto;
  padding: 10px 16px 120px;
}

/* CARD */
.exercise-card {
  background: #6e2a2a;
  border-radius: 24px;
  padding: 16px;
  margin-bottom: 16px;
  color: white;
}

/* HEADER ROW */
.exercise-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}

/* EXERCISE TITLE */
.exercise-title {
  flex: 1;
  background: #e7bcbc;
  color: #2a0f0f;
  padding: 10px 14px;
  border-radius: 999px;
  border: none;
  outline: none;
  font-weight: 600;
}

/* DELETE EXERCISE */
.delete-exercise {
  margin-left: 10px;
  width: 34px;
  height: 34px;
  border-radius: 50%;
  border: none;
  background: #2b0b0b;
  color: white;
  cursor: pointer;
}

/* GRID */
.grid {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr 1fr 60px;
  gap: 8px;
  align-items: center;
  font-size: 13px;
}

.header {
  font-weight: bold;
  text-transform: uppercase;
  margin-bottom: 8px;
}

/* INPUTS */
.row input {
  width: 100%;
  padding: 6px;
  border-radius: 6px;
  border: none;
  text-align: center;
}

/* LOCKED */
.locked {
  background: #3b1414;
  padding: 6px;
  border-radius: 6px;
  text-align: center;
}

/* ACTIONS */
.actions {
  display: flex;
  gap: 6px;
  justify-content: center;
}

/* CHECK */
.check {
  width: 26px;
  height: 26px;
  border-radius: 50%;
  border: none;
  background: #3b1414;
  color: white;
  cursor: pointer;
}

.check.done {
  background: green;
}

/* DELETE SET */
.delete {
  width: 26px;
  height: 26px;
  border-radius: 50%;
  border: none;
  background: #2b0b0b;
  color: white;
  cursor: pointer;
}

/* ADD SET */
.add-set {
  width: 100%;
  margin-top: 12px;
  padding: 10px;
  border-radius: 999px;
  border: none;
  background: #e7bcbc;
  color: #2a0f0f;
  font-weight: 600;
  cursor: pointer;
}

/* ADD EXERCISE */
.add-exercise {
  width: 100%;
  margin-top: 10px;
  padding: 14px;
  border-radius: 999px;
  border: none;
  background: #5b1f1f;
  color: white;
  font-weight: 700;
  cursor: pointer;
}
</style>