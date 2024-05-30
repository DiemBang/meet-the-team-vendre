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
    <div class="portraits">
        <div class="portrait-container" v-for="user in users">
            <Portrait :firstName="user.first_name" :lastName="user.last_name" :contact="user.contact" :img="user.avatar" />
        </div>
    </div>
</template>