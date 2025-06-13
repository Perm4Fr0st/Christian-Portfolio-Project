<template>
  <section
    id="skills"
    class="min-vh-10 vw-100 scroll-offset"
    :class="isDark ? 'bg-black text-white' : 'bg-light text-dark'"
  >
    <div class="container">
      <h2 class="text-center mb-5">My Skills</h2>

      <div id="skillsCarousel" class="carousel slide" data-bs-ride="carousel">
        <div class="carousel-inner text-center">
          <div
            v-for="(skillGroup, index) in skills"
            :key="index"
            class="carousel-item"
            :class="{ active: index === 0 }"
          >
            <div class="row justify-content-center">
              <div
                v-for="(skill, i) in skillGroup"
                :key="i"
                class="col-6 col-md-4 col-lg-3 mb-4"
              >
                <div
                  class="p-3 border rounded shadow-sm h-100"
                  :class="isDark ? 'bg-white text-dark' : 'bg-dark text-white'"
                >
                  <img
                    :src="skill.icon"
                    :alt="skill.name"
                    class="img-fluid mb-2"
                    style="height: 50px;"
                  />
                  <h5>{{ skill.name }}</h5>
                </div>
              </div>
            </div>
          </div>
        </div>

        <button
          class="carousel-control-prev"
          type="button"
          data-bs-target="#skillsCarousel"
          data-bs-slide="prev"
        >
          <span class="carousel-control-prev-icon"></span>
        </button>
        <button
          class="carousel-control-next"
          type="button"
          data-bs-target="#skillsCarousel"
          data-bs-slide="next"
        >
          <span class="carousel-control-next-icon"></span>
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import htmlIcon from '../assets/img/html-5.png'
import cssIcon from '../assets/img/css3.png'
import jsIcon from '../assets/img/js.png'
import bootstrapIcon from '../assets/img/bootstrap.png'
import nodeIcon from '../assets/img/node-js.png'
import phpIcon from '../assets/img/php.png'
import laravelIcon from '../assets/img/laravel.png'
import vueIcon from '../assets/img/vue.png'
import gitIcon from '../assets/img/git.png'
import dockerIcon from '../assets/img/docker.png'
import githubIcon from '../assets/img/github.png'
import sqlIcon from '../assets/img/sql.png'
const isDark = ref(false)
const updateDarkMode = () => {
  isDark.value = document.body.classList.contains('dark-mode')
}
onMounted(() => {
  updateDarkMode()
  const observer = new MutationObserver(updateDarkMode)
  observer.observe(document.body, { attributes: true, attributeFilter: ['class'] })
})

const skills = ref([
  [
    { name: 'HTML5', icon: htmlIcon },
    { name: 'CSS3', icon: cssIcon },
    { name: 'JavaScript', icon: jsIcon },
    { name: 'Bootstrap', icon: bootstrapIcon }
  ],
  [
    { name: 'Node.js', icon: nodeIcon },
    { name: 'PHP', icon: phpIcon },
    { name: 'Laravel', icon: laravelIcon },
    { name: 'Vue.js', icon: vueIcon }
  ],
    [
    { name: 'Git', icon: gitIcon },
    { name: 'Docker', icon: dockerIcon },
    { name: 'Github', icon: githubIcon },
    { name: 'SQL', icon: sqlIcon }
  ]
])
</script>

<style scoped>
.carousel-control-prev-icon,
.carousel-control-next-icon {
  background-color: rgba(0, 0, 0, 0.5);
  border-radius: 50%;
}
</style>
