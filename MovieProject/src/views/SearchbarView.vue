<script setup>
    //fetch data from API and display search results 
    //update movie poster scroll view with search results - including poster image, title, release date, actors, director, genre, and rating
    //if exact match is found - no pagination necessary
    //implement pagination for search results if necessary (show matches with release date, genre in dropdown from search bar)
</script>
<template>
    <form class="search-form">
        <input type="text" placeholder="Search for movies..." />
        <button type="submit">Search</button>
    </form>
</template>
<style scoped>
 .search-form {
    margin-top: 2rem;
    display: flex;
    width: clamp (100%, 400px, 500px);
    font-size: 1rem;
    background-color: var(--dark-movietheater);
    color: var(--light-movie-credits-white);
    border: 1px solid var(--light-movie-credits-white);
    border-radius: 4px;
    padding: 0.5rem;
    }
</style>