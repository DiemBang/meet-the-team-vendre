<script setup>
import { ref } from 'vue';
//import HelloWorld from './components/HelloWorld.vue'
import Portrait from './Portrait.vue';
import axios from "axios";

const apiUrl = "https://reqres.in/api/users";
const users = ref([]);
let currentPage = ref(1);
const totalPages = ref(0);

const getUsers = async (page) => {
    let url = apiUrl +"?page="+page;
  await axios.get(url).then((response) => {
    console.log(response);
    users.value = response.data.data
    totalPages.value = response.data.total_pages
  })
}
getUsers(currentPage.value);

const goToNextPage = () => {
    currentPage.value += 1;
    getUsers(currentPage.value);
}

const goToPreviousPage = () => {
    currentPage.value -= 1;
    getUsers(currentPage.value);    
}
</script>

<template>  
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@24,400,0,0" />
    <div class="page-background">
        <h1>Our Team</h1>
    
        <div class="portraits">
            <div class="portrait-container" v-for="user in users">
            <Portrait :firstName="user.first_name" :lastName="user.last_name" :contact="user.contact" :img="user.avatar" />
            </div>
        </div>
        <button id="nextPage" @click="goToNextPage()" :class="{hidden:currentPage===totalPages}">Next page</button>
        <button id="previousPage" @click="goToPreviousPage()" :class="{hidden:currentPage===1}">Previous page</button>
    </div>
</template>

<style scoped>

.page-background {
    width: 100%;
}

.hidden {
    display: none;
}
</style>

<style>

</style>