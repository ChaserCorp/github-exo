<template>
    <nav class="navbar">
        <ul>
            <li><router-link to="/">Home</router-link></li>
            <li><router-link to="/favorites">Favoris</router-link></li>
        </ul>
    </nav>
</template>

<script lang="ts">
export default {
    name: 'Navbar',
};
</script>

<style>
.navbar {
    display: flex;
    justify-content: space-around;
    background: #333;
    color: white;
    padding: 10px;
    width: 100%;
}
ul {
    list-style: none;
    display: flex;
    gap: 15px;
}
</style>
