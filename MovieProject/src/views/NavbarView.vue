<script setup>
import { ref } from 'vue'
import { RouterLink } from 'vue-router'

const isMenuOpen = ref(false)

</script>

<template>
    <nav class="navbar">
        <div class="navbarLogo">
            <h1 class="logo">MovieProject</h1>
        </div>

        <!-- Desktop Links -->
        <ul class="navbarLinks desktop">
            <li><RouterLink to="/">Home</RouterLink></li>
            <li><RouterLink to="/movies">Movies</RouterLink></li>
            <li><RouterLink to="/reviews">Reviews</RouterLink></li>
            <li><RouterLink to="/about">About</RouterLink></li>
        </ul>

        <!-- Hamburger -->
        <button class="hamburger" @click="isMenuOpen = !isMenuOpen" aria-label="Toggle menu">
        <span :class="{ open: isMenuOpen }"></span>
        <span :class="{ open: isMenuOpen }"></span>
        <span :class="{ open: isMenuOpen }"></span>
        </button>

        <!-- Mobile Dropdown -->
        <ul class="navbarLinks mobile" v-if="isMenuOpen">
            <li><RouterLink to="/">Home</RouterLink></li>
            <li><RouterLink to="/movies">Movies</RouterLink></li>
            <li><RouterLink to="/reviews">Reviews</RouterLink></li>
            <li><RouterLink to="/about">About</RouterLink></li>
        </ul>

    </nav>

</template>

<style scoped>

:root {
    --dark-movietheater: #0b0c10;
    --light-movie-credits-white: #c5c6c7;
    --popcorn-butter-yellow: #f0e400;
}

.navbar {   position: sticky;
  top: 0;
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 0.8rem 1rem;
  background-color: var(--dark-movietheater);
  color: var(--light-movie-credits-white);
  backdrop-filter: blur(8px);
  box-sizing: border-box;
  overflow: visible; 
}

.navbar * {
  box-sizing: border-box; 
}

.navbarLogo .logo {
  font-size: 1.5rem;
  font-weight: bold;
}

.navbarLinks {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  gap: 1.2rem;                       /* smaller gap on desktop/mobile */
}

.navbarLinks li a {
  color: var(--light-movie-credits-white);
  text-decoration: none;
  font-size: 1rem;
  transition: color 0.3s ease;
}

.navbarLinks li a:hover {
  color: var(--popcorn-butter-yellow);
}

/* Hamburger – make sure it's fully visible */
.hamburger {
  display: none;
  flex-direction: column;
  justify-content: space-around;
  width: 40px;                       
  height: 40px;
  background: transparent;
  border: none;
  cursor: pointer;
  gap: 8px;
  padding: 8px;
  margin-left: auto;                 
  flex-shrink: 0;
}

.hamburger span {
  width: 100%;
  height: 4px;
  background: var(--textColor-light-moonlitSnow);
  transition: all 0.3s ease;
  border-radius: 2px;                
}


.hamburger span.open:nth-child(1) { transform: rotate(45deg) translate(7px, 7px); }
.hamburger span.open:nth-child(2) { opacity: 0; }
.hamburger span.open:nth-child(3) { transform: rotate(-45deg) translate(7px, -7px); }

/* Mobile menu – ensure it's visible when rendered */
.mobile {
  display: none !important;          
  flex-direction: column;
  position: absolute;           
  right: 1rem;
  background-color: var(--dark-movietheater); 
  padding: 1rem;
  border-radius: 8px;
  gap: 1rem;
  width: clamp(70vw, 80vw, 270px);
  overflow: visible;
}

/* On mobile: show hamburger, hide desktop*/
@media only screen and (max-width: 768px) {
  .desktop {
    display: none !important;
  }
  .hamburger {
    display: flex !important;
  }
  
  .mobile {
    display: flex !important;
  }
  .app-navbar {
    padding: 0.6rem 0.8rem;         
  }
}




</style> 