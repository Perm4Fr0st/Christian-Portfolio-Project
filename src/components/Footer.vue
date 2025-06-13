<template>
  <footer
    class="min-vh-10 vw-100 py-5 text-center"
    :class="isDark ? 'bg-black text-white' : 'bg-light text-dark'"
  >
    <div class="container">
      <p class="mb-2">&copy; {{ new Date().getFullYear() }} Christian Alba. All rights reserved.</p>
      
      <div class="d-flex justify-content-center gap-3">
        <a
          href="https://github.com/Perm4Fr0st"
          target="_blank"
          rel="noopener"
          class="text-decoration-none"
          :class="isDark ? 'text-white' : 'text-dark'"
        >
          <i class="bi bi-github fs-4"></i>
        </a>
        <a
          href="https://www.linkedin.com/in/christian-alfred-alba-76068027b/"
          target="_blank"
          rel="noopener"
          class="text-decoration-none"
          :class="isDark ? 'text-white' : 'text-dark'"
        >
          <i class="bi bi-linkedin fs-4"></i>
        </a>
        <a
          href="mailto:Christianalfredalba26@gmail.com"
          class="text-decoration-none"
          :class="isDark ? 'text-white' : 'text-dark'"
        >
          <i class="bi bi-envelope fs-4"></i>
        </a>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isDark = ref(false)

const updateDarkMode = () => {
  isDark.value = document.body.classList.contains('dark-mode')
}

onMounted(() => {
  updateDarkMode()
  const observer = new MutationObserver(updateDarkMode)
  observer.observe(document.body, {
    attributes: true,
    attributeFilter: ['class']
  })
})
</script>

<style scoped>
footer a:hover {
  opacity: 0.8;
}
</style>
