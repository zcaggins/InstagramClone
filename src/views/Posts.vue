<script setup>

import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
import { ref } from 'vue';

let posts = ref([])

fetch('http://localhost:3000/posts',
{
    headers: {'Authorization': document.cookie},
})
.then(response => {
    return response.json()
})
.then(json => {
    posts.value.push(...json)
    console.log(json)
})
.catch(error => {
    console.log(error)
})
</script>

<template>
    <div id="page-container">
        <Header></Header>  
        <div v-for="post in posts">
            <div class="post-container">
                <div class="post">
                    <div class="card-header">
                        <p>{{ post.username }}</p>
                    </div>
                    <div class="card-image-container">
                        <img :src= "post.image" id="picture">
                    </div>
                    <div class="card-footer">
                        <div class="likes-container">
                            <p>Likes: {{ post.likes.length }}</p>
                            <p>❤️</p>
                        </div>
                        <div class="caption-container">
                            <p> {{ post.caption }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
       
    </div>


</template>


<style scoped>
p {
    color: white;
    font-size: 25px;
}
#page-container {
    background-color: black;
    margin: 0;
    
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
.post-container{
    background-color: black;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 1rem 10rem;
    
}
#picture {
    height: 35rem;
    width: 38rem;
}

</style>