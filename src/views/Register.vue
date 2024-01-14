<script setup>
import router from '@/router';
import { ref } from 'vue'
import { RouterLink } from 'vue-router';
const email = ref('')
const username = ref('')
const password = ref('')

function register() {
  const reqBody = {
    "email": email.value,
    "username": username.value,
    "password": password.value
  }
  fetch("http://localhost:3000/users", 
  {
    headers: {"Content-Type": "application/json"},
    body: JSON.stringify(reqBody),
    method: "POST"
  })

  .then(response => {
    if(response.status === 201) {
      alert("Account Created: Please login to continue")
      router.push("/")
    } else {
      alert("Something went wrong! Please try again")
    }
  })

  .catch(error => {
    console.log(error)
  })
}

</script>

<template>
    <div class="container">
  <img src="../assets/instagram-script.webp" alt="iglogo">
  <input v-model="email" id="email" type="text" placeholder="Email">
  <input v-model="username" id="username" type="text" placeholder="Username">
  <input v-model="password" id="password" type="text" placeholder="Password">

  
  <button @click="register" id="sign-up">Sign Up</button>
  <RouterLink to="/">Cancel</RouterLink>
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