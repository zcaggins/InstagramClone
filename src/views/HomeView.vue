<script setup>
import router from '@/router';
import { ref } from 'vue'
import { RouterLink } from 'vue-router';

let email = ref('')
let password = ref('')

function login() {
  const reqBody = {
    "email": email.value,
    "password": password.value
  }

  fetch("http://localhost:3000/login", 
  {
    headers: {"Content-Type": "application/json"},
    body: JSON.stringify(reqBody),
    method: "POST"
  })

  .then(response => {
    return response.json()
  })
  .then(json => {
    document.cookie = json
    router.push('/posts')
    console.log(json)
  })
  .catch(error => {
    console.log(error)
  })
}

</script>

<template>
  <div class="container">
  <img src="../assets/instagram-script.webp" alt="iglogo">

  <input v-model="email" id="username" type="text" placeholder="Email">
  <input v-model="password" id="password" type="text" placeholder="Password">
  
  <button @click="login" id="login">Login</button>
  <RouterLink to="/register">Register</RouterLink>
</div>
</template>

<style scoped>

img {
  display: flex;
  height: 16rem;
  width: 24rem;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  gap: 30px;
  /* margin: 175px 450px; */
  /* border: 1px solid gray; */
}

h1 {
  text-align: center;
}

.register {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#login {
  background-color: lightblue;
  width: 150px;
}










</style>
