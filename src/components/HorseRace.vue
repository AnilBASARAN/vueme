<template>
  <section id="events" class="race-container">
    <header>
      <h1>Vue + GSAP Horse Race</h1>
    </header>

    <!-- control buttons -->
    <div class="controls">
      <button @click="startRace">Start Race</button>
      <button @click="resetRace">Reset</button>
    </div>

    <!-- racetrack -->
    <div class="race-track">
      <div
        v-for="(horse, idx) in horses"
        :key="idx"
        class="horse"
      >
        🐎 {{ idx + 1 }}
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import gsap from 'gsap'

// reactive refs
const horses = ref([1, 2, 3, 4, 5])
let raceTimeline = null

function buildRace() {
  // clear any existing timeline
  if (raceTimeline) {
    raceTimeline.kill()
    gsap.set('.horse', { x: 0 })
  }

  raceTimeline = gsap.timeline()
  const nodes = document.querySelectorAll('.horse')

  nodes.forEach((el) => {
    const duration = gsap.utils.random(3, 5)
    const easePower = gsap.utils.random(1, 4, 1)
    raceTimeline.to(el, {
      x: window.innerWidth - el.offsetWidth - 20,
      duration,
      ease: `power${easePower}.in`
    }, 0)
  })
}

function startRace() {
  if (!raceTimeline) buildRace()
  raceTimeline.restart()
}

function resetRace() {
  if (raceTimeline) raceTimeline.pause(0)
  gsap.set('.horse', { x: 0 })
}

onMounted(() => {
  // style and fade-in horses like the CodePen
  gsap.set('.horse', {
    backgroundColor: gsap.utils.wrap([
      '#c21216','#3d8000','#007980','#002a80','#ae00b1'
    ]),
    opacity: 1
  })
  gsap.from('.horse', {
    opacity: 0,
    scale: 0.8,
    stagger: 0.1,
    duration: 0.5
  })
})
</script>

<style scoped>
.race-container {
  max-width: 800px;
  margin: 1rem auto;
  text-align: center;
}

.controls {
  margin-bottom: 1rem;
}

.controls button {
  margin: 0 0.5rem;
  padding: 0.5rem 1rem;
}

.race-track {
  position: relative;
  height: 200px;
  background: #eee;
  border: 2px solid #ccc;
  overflow: hidden;
}

.horse {
  position: absolute;
  left: 0;
  width: 60px;
  height: 40px;
  line-height: 40px;
  text-align: center;
  border-radius: 4px;
  color: white;
  font-weight: bold;
}

.horse:nth-child(1) { top: 10px; }
.horse:nth-child(2) { top: 60px; }
.horse:nth-child(3) { top: 110px; }
.horse:nth-child(4) { top: 160px; }
.horse:nth-child(5) { top: 210px; }
</style>
