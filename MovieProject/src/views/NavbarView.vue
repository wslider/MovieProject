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



</style> 