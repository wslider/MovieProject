<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const currentStep = ref(1)
let observer = null

onMounted(() => {
  const movieEl = document.querySelector('.movie')
  const sections = document.querySelectorAll('.scroll-section')

  observer = new IntersectionObserver(
    (entries) => {
      const visibleEntry = entries
        .filter(e => e.isIntersecting)
        .sort((a, b) => a.boundingClientRect.top - b.boundingClientRect.top)[0]

      if (visibleEntry) {
        const index = Array.from(sections).indexOf(visibleEntry.target) + 1
        currentStep.value = index
        movieEl.className = 'movie'
        movieEl.classList.add(`step-${index}`)
      }
    },
    {
      root: null,
      threshold: [0.4, 0.6, 0.8],
      rootMargin: '-20% 0px -30% 0px'
    }
  )

  sections.forEach(section => observer.observe(section))
})

onUnmounted(() => {
  if (observer) observer.disconnect()
})
</script>

<template>
  <main class="scroll-container">
    <section class="scroll-section"></section>
    <section class="scroll-section"></section>
    <section class="scroll-section"></section>
  </main>

  <div class="movie" :class="`step-${currentStep}`">
    <div class="bg">
      <img
        src="https://m.media-amazon.com/images/I/81C7fjFH3HL.jpg"
        alt="Featured movie poster"
        loading="eager"
      />
    </div>

    <div class="content-layer step-1">
      <div class="content-box">
        <h1>Interstellar</h1>
        <p>
          In Earth's future, a global crop blight and second Dust Bowl are slowly rendering the planet uninhabitable. 
          Professor Brand, a brilliant NASA physicist, is working on plans to save mankind by transporting Earth's population to a new home via a wormhole.
        </p>
      </div>
    </div>

    <div class="content-layer step-2">
      <div class="content-box">
        <h1>The Mission</h1>
        <p>
          Former NASA pilot Cooper is tasked to lead a team through the wormhole near Saturn to explore three potentially habitable planets. 
          The journey tests the limits of human endurance, love, and the laws of physics itself.
        </p>
      </div>
    </div>

    <div class="content-layer step-3">
      <div class="content-box credits">
        <div class="credit-item">
          <h3>Director</h3>
          <p>Christopher Nolan</p>
        </div>
        <div class="credit-item">
          <h3>Writers</h3>
          <p>Jonathan Nolan, Christopher Nolan</p>
        </div>
        <div class="credit-item">
          <h3>Stars</h3>
          <p>Matthew McConaughey, Anne Hathaway, Jessica Chastain</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.movie {
  position: fixed;
  inset: 0;
  background: #000;
  color: #fff;
  overflow: hidden;
  pointer-events: none;
  z-index: -1;
}

.bg {
  position: absolute;
  inset: 0;
  display: grid;
  place-items: center;
}

.bg img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transform: scale(1.4);
  transition: transform 2s cubic-bezier(0.16, 1, 0.3, 1);
  will-change: transform;
  backface-visibility: hidden;
}

.content-layer {
  position: absolute;
  inset: 0;
  display: grid;
  place-items: center;
  background: linear-gradient(to bottom, rgba(0,0,0,0.4), rgba(0,0,0,0.75));
  padding: 6vw;
  opacity: 0;
  transition: opacity 1.2s ease, transform 1.5s ease;
  transform: translateY(60px) scale(0.92);
  pointer-events: none;
}

.content-box {
  max-width: 780px;
  text-align: center;
  font-family: 'Helvetica Neue', Arial, sans-serif;
}

.credits {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 5rem 7rem;
}

.credit-item {
  min-width: 260px;
  text-align: left;
}

h1, h3 {
  margin-bottom: 0.8em;
  font-weight: 700;
  letter-spacing: 1px;
}

.movie.step-1 .content-layer.step-1,
.movie.step-2 .content-layer.step-2,
.movie.step-3 .content-layer.step-3 {
  opacity: 1;
  transform: translateY(0) scale(1);
  pointer-events: auto;
}

.movie.step-1 .bg img { transform: scale(1.40); }
.movie.step-2 .bg img { transform: scale(1.20); }
.movie.step-3 .bg img { transform: scale(1.00); }

.scroll-container {
  position: relative;
  z-index: 1;
  background: transparent;
}

.scroll-section {
  height: 100vh;
}
</style>

<style>
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  background: transparent !important;
}
</style>