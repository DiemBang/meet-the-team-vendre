<script setup>
import { ref } from 'vue';
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
            <Portrait :firstName="user.first_name" :lastName="user.last_name" :contact="user.email" :img="user.avatar" />
            </div>
        </div>
        <button id="nextPage" @click="goToNextPage()" :class="{hidden:currentPage===totalPages}">Next Page</button>
        <button id="previousPage" @click="goToPreviousPage()" :class="{hidden:currentPage===1}">Previous Page</button>
    </div>
</template>

<style scoped>

.page-background {
    
    margin: 0;
    padding: 0;
}

.hidden {
    display: none;
}

/* Desktop */
@media screen and (min-width: 1280px) {
    
    .portraits {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        padding: 20px;
        box-sizing: border-box;
    }
    .portrait-container {
        flex-basis: 33%;
        text-align: center;
        margin: 0;
        padding: 20px;
        box-sizing: border-box;
    }
}

/* Tablet in landscape mode */
  @media screen and (min-width: 768px) and (max-width: 1367px) and (orientation: landscape) {
    .portraits {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        padding: 20px;
        box-sizing: border-box;
    }
    .portrait-container {
        flex-basis: 33%;
        text-align: center;
        margin: 0;
        padding: 20px;
        box-sizing: border-box;
    }
  } 

/* Tablet in portrait mode */
@media screen and (min-width: 768px) and (max-width: 1279px) and (orientation: portrait) {
    .portraits {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        padding: 20px;
        box-sizing: border-box;
    }
    .portrait-container {
        flex-basis: 50%;
        text-align: center;
        margin: 0;
        padding: 20px;
        box-sizing: border-box;
    }
}

</style>

