<template>
  <section
    id="home"
    class="min-vh-100 vw-100"
    :class="['d-flex align-items-center', isDark ? 'bg-black text-white' : 'bg-light text-dark']"
  >
    <div class="container">
      <transition name="fade-slide" appear>
        <div class="row align-items-center">
          <!-- Left Content -->
          <div class="col-lg-6 text-center text-lg-start">
            <p class="fs-5 mb-3">Hi, I'm Christian Alba!</p>
            <h1 class="display-4 fw-bold mb-3">
              I Build & Design <br />
              Web Interfaces.
            </h1>
            <!-- <p class="lead mb-4">
             
            </p> -->
          </div>

          <!-- Right Image -->
          <div class="col-lg-6 text-center mt-4 mt-lg-0">
            <img
              src="../assets/img/6.png"
              alt="Profile picture"
              class="img-fluid rounded shadow"
              style="max-height: 600px;"
            />
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
  // Watch for class changes in body (works when toggled)
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
