<script setup>
import { ref } from 'vue'
//import HelloWorld from './components/HelloWorld.vue'
import Portrait from './Portrait.vue'
import axios from "axios";

const apiUrl = "https://reqres.in/api/users";
const users = ref([]);

const getUsers = async () => {
  await axios.get(apiUrl).then((response) => {
    users.value = response.data.data
    console.log(response.data)
  })
}
getUsers()

</script>

<template>  
    <h1>Our Team</h1>
    <div v-for="user in users">
        <Portrait :name="user.first_name" :contact="user.contact" />
    </div>
</template>