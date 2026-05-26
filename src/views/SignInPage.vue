<template>
  <div class="wrapper">
    <div class="content">
      <img class="logo" :src="logo" alt="Fiter logo" />

      <button
        class="btn-back"
        type="button"
        @click="goBack"
        aria-label="Go back"
      >
        ←
      </button>

      <div class="form-card">
        <label for="name">Name</label>
        <input id="name" type="text" placeholder="Enter your name" />

        <label for="email">Email</label>
        <input id="email" type="email" placeholder="Enter your email" />

        <label for="password">Password</label>
        <input
          id="password"
          type="password"
          placeholder="Enter your password"
        />

        <button class="btn-submit">Create</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import logo from '../assets/fiterlogo.png'
import { useRouter } from 'vue-router'

const router = useRouter()

function goBack() {
  router.back()
}
</script>

<style>
* {
  box-sizing: border-box;
}

html,
body,
#app {
  height: 100%;
  margin: 0;
  overflow: hidden;

  background: linear-gradient(
    to bottom,
    #1f1f1f 30%,
    #8b0000 100%
  );
}

.wrapper {
  min-height: 100dvh;
  height: 100vh;
  overflow: hidden;
  display: flex;
  justify-content: center;
  padding: 6px 16px;
}

.content {
  width: min(420px, 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  transform: translateY(-100px);
}

.logo {
  width: 100%;
  max-width: 393px;
  height: auto;
  display: block;
}

.btn-back {
  align-self: flex-start;
  margin-top:0;
  margin-bottom: 4px;
  border: none;
  background: transparent;
  color: #111;
  font-size: 44px;
  line-height: 1;
  padding: 0;
  cursor: pointer;
}

.form-card {
  background: #c40000;
  padding: 20px;
  border-radius: 12px;
  border: 2px solid black;
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 12px;
  box-shadow: 0 6px 18px rgba(0, 0, 0, 0.35);
 
  color: black;
  font-size: 16px;
}

.form-card label {
  color: #111;
  font-weight: 600;
}

.form-card input {
  padding: 12px;
  border-radius: 8px;
  border: none;
  background: #e0e0e0;
  width: 100%;
  font-size: 16px;
}

.btn-submit {
  margin-top: 10px;
  padding: 12px;
  border-radius: 10px;
  border: 2px solid black;
  background: rgb(31, 30, 30);
  color: white;
  width: 100%;
  cursor: pointer;
  font-weight: 700;
  font-size: 16px;
  transition: 0.2s ease;
}

.btn-submit:hover {
  transform: scale(1.02);
}
</style>