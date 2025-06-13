<template>
  <section
    id="about"
    class="min-vh-80 vw-100 py-5"
    :class="['d-flex align-items-center', isDark ? 'bg-black text-white' : 'bg-light text-dark']"
  >
    <div class="container">
      <transition name="fade-slide" appear>
        <div class="row align-items-center">
          <!-- Left Image -->
          <div class="col-lg-6 text-center mb-4 mb-lg-0">
            <img
              src="../assets/img/about.jpg"
              alt="About me image"
              class="img-fluid rounded shadow"
              style="max-height: 500px;"
            />
          </div>

          <!-- Right Content -->
          <div class="col-lg-6">
            <h2 class="fw-bold mb-4">About Me</h2>
            <p class="lead">
              I'm Christian Alba, a passionate web developer with a strong focus on
              building intuitive and dynamic user interfaces. I enjoy transforming
              ideas into responsive and functional web experiences.
            </p>
            <p>
              With a background in both design and development, I bridge the gap between
              creativity and technology. I specialize in JavaScript frameworks, backend
              integration, and modern web standards.
            </p>
            <p>
              Outside of coding, I love exploring new technologies, contributing to open
              source, and sharing knowledge with the community.
            </p>
          </div>
        </div>
      </transition>
    </div>
  </section>
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
  observer.observe(document.body, { attributes: true, attributeFilter: ['class'] })
})
</script>

<style scoped>
.fade-slide-enter-active {
  transition: opacity 0.8s ease, transform 0.8s ease;
}
.fade-slide-enter-from {
  opacity: 0;
  transform: translateY(100px);
}
.fade-slide-enter-to {
  opacity: 1;
  transform: translateY(0);
}
</style>
