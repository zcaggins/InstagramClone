<script setup>

</script>

<template>
    <div id="header">
        <img id="logo" src="" alt="">
        <RouterLink to="/posts">Home</RouterLink>
        <RouterLink to="/create-post">Create</RouterLink>
        <RouterLink to="/profile">Profile</RouterLink>
    </div>



</template>

<style setup>
#header {
    height: 2rem;
    width: 100vw;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    font-size: 1.5rem;
};

#logo {
    height: 1rem;
    width: 1rem;
}

</style>