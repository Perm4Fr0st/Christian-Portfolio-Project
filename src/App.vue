<script setup>
import { ref, onMounted, watch } from 'vue'
import Header from './components/Header.vue'
import Home from './components/Home.vue'
import Skill from './components/Skill.vue'
import About from './components/About.vue'
import Footer from './components/Footer.vue'

const isDark = ref(false)

const toggleDarkMode = () => {
  isDark.value = !isDark.value

  // Add a small delay to feel the transition
  setTimeout(() => {
    document.body.classList.toggle('dark-mode', isDark.value)
  }, 100)
}

// Load saved theme from localStorage
onMounted(() => {
  isDark.value = localStorage.getItem('darkMode') === 'true'
  document.body.classList.toggle('dark-mode', isDark.value)
})

// Persist setting when isDark changes
watch(isDark, (newValue) => {
  localStorage.setItem('darkMode', newValue)
})

</script>

<template>
  
  <Header />
  
  <section id="home">
    <Home />
  </section>
  
  <section id="skill">
    <Skill />
  </section>
  
  <section id="about">
    <About />
  </section>
  
  <section id="contact">
    <Footer />
  </section>
</template>


<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
