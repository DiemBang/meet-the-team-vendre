<script setup>
import { ref } from 'vue';
//import HelloWorld from './components/HelloWorld.vue'
import Portrait from './Portrait.vue';
import axios from "axios";

const apiUrl = "https://reqres.in/api/users";
const users = ref([]);
let currentPage = ref(1);

const getUsers = async (page) => {
    let url = apiUrl +"?page="+page;
  await axios.get(url).then((response) => {
    users.value = response.data.data
    console.log(response.data)
  })
}
getUsers(currentPage.value);

const goToNextPage = () => {
    currentPage.value = 2;
    getUsers(currentPage.value);    
}

const goToPreviousPage = () => {
    currentPage.value = 1;
    getUsers(currentPage.value);    
}
</script>

<template>  
    <h1>Our Team</h1>
    <div class="portraits">
        <div class="portrait-container" v-for="user in users">
            <Portrait :firstName="user.first_name" :lastName="user.last_name" :contact="user.contact" :img="user.avatar" />
        </div>
    </div>
    <button id="nextPage" @click="goToNextPage()" :class="{hidden:currentPage===2}">Next page</button>
    <button id="previousPage" @click="goToPreviousPage()" :class="{hidden:currentPage===1}">Previous page</button>
</template>

<style scoped>
.hidden {
    display: none;
}
</style>