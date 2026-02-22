<script setup lang="ts">
import { ref, onMounted } from 'vue'

const message = ref<string>('Loading...')
const error = ref<string | null>(null)

const fetchMessage = async () => {
  try {
    error.value = null
    const response = await fetch('/api/hello')
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`)
    }
    const data = await response.json()
    message.value = data.message
  } catch (e: any) {
    console.error('Failed to fetch message:', e)
    error.value = 'Failed to fetch from backend. Is the FastAPI server running?'
  }
}

onMounted(() => {
  fetchMessage()
})
</script>

<template>
  <div class="container">
    <div class="card">
      <div class="logo-container">
        <a href="https://vuejs.org/" target="_blank">
          <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
        </a>
        <a href="https://fastapi.tiangolo.com/" target="_blank">
          <img src="https://fastapi.tiangolo.com/img/logo-margin/logo-teal.png" class="logo fastapi" alt="FastAPI logo" />
        </a>
      </div>
      
      <h1>Vue + FastAPI</h1>
      
      <div class="message-box">
        <h2>Backend Response:</h2>
        <p v-if="error" class="error">{{ error }}</p>
        <p v-else class="message">{{ message }}</p>
      </div>
      
      <button @click="fetchMessage" class="action-btn">
        Refresh Message
      </button>

      <p class="docs">
        Check <a href="http://127.0.0.1:8000/docs" target="_blank">FastAPI Docs</a> for interactive API testing.
      </p>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #1a1a1a;
  color: #ffffff;
  font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
}

.card {
  background: #2a2a2a;
  padding: 3rem;
  border-radius: 16px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
  text-align: center;
  max-width: 600px;
  width: 100%;
}

.logo-container {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 2rem;
  margin-bottom: 2rem;
}

.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.logo.fastapi {
  height: 5em; /* Adjust to match vue logo visually */
}
.logo.fastapi:hover {
  filter: drop-shadow(0 0 2em #009688aa);
}

h1 {
  font-size: 3.2em;
  background: -webkit-linear-gradient(315deg, #42d392 25%, #647eff);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin: 0;
}

.message-box {
  margin: 2rem 0;
  padding: 1.5rem;
  background: #333;
  border-radius: 8px;
  border-left: 4px solid #42b883;
}

h2 {
  font-size: 1.2em;
  color: #aaa;
  margin-top: 0;
}

.message {
  font-size: 1.5em;
  font-weight: bold;
  color: #42b883;
}

.error {
  color: #ff5555;
  font-weight: bold;
}

.action-btn {
  background-color: #42b883;
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  font-size: 1.1em;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.2s, transform 0.1s;
}

.action-btn:hover {
  background-color: #33a06f;
}

.action-btn:active {
  transform: scale(0.98);
}

.docs {
  margin-top: 2rem;
  color: #888;
}

.docs a {
  color: #646cff;
  text-decoration: none;
}

.docs a:hover {
  text-decoration: underline;
}
</style>
