<template>
  <nav class="navbar navbar-expand-lg fixed-top" :class="isDark ? 'navbar-dark bg-dark' : 'navbar-light bg-light'">
    <div class="container-fluid px-4">
      <a class="navbar-brand fw-bold" href="#">MySite</a>

      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">About</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Contact</a>
          </li>
        </ul>
        <button class="btn btn-outline-secondary" @click="toggleDarkMode">
          {{ isDark ? 'Light Mode' : 'Dark Mode' }}
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue'

const isDark = ref(false)

const toggleDarkMode = () => {
  isDark.value = !isDark.value
  document.body.classList.toggle('dark-mode', isDark.value)
}

onMounted(() => {
  isDark.value = localStorage.getItem('darkMode') === 'true'
  document.body.classList.toggle('dark-mode', isDark.value)
})

watch(isDark, (val) => {
  localStorage.setItem('darkMode', val)
})
</script>

<style scoped>
.navbar {
  transition: background-color 0.4s ease;
}
</style>
