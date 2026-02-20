<script setup>
</script>

<template>
  <header class="home-header">
    <div class="home-container">
      <h1>Welcome to MovieProject</h1>
      <p>Discover movies, read reviews, and stay updated with the latest in cinema.</p>
    </div>
    <form class="search-form">
      <input type="text" placeholder="Search for movies..." />
      <button type="submit">Search</button>
    </form>
  </header>
</template>

<style scoped>
  .home-header {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 4rem 1rem;
    background-color: var(--dark-movietheater);
    color: var(--light-movie-credits-white);
    text-align: center;
    box-sizing: border-box;
    width: 100%;
  }

  .search-form {
    margin-top: 2rem;
    display: flex;
    width: clamp (100%, 400px, 500px);
    font-size: 1rem;
  }
</style>
