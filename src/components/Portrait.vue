<script setup>
import { ref } from 'vue'

defineProps({
  firstName: String,
  lastName: String,
  contact: String,
  img: String
})

</script>

<template>
    <section class="portrait">
        <div class="img-container">
            <img :src="img" alt="Photo of the team member">
        </div>
        <div class="name">{{ firstName + ' ' + lastName }}</div>
        <div class="contact"><span class="material-symbols-outlined">mail</span><a :href="`mailto:${contact}`">Contact me</a></div>
    </section>
</template>

<style scoped>

.portrait {
  display: flex;
  flex-direction: column; /* Align items vertically */
  align-items: center; /* Center horizontally */
  margin: 1.3rem;
}

.contact {
    display: flex;
    align-items: center;
}

.material-symbols-outlined {
    margin-right: 0.5rem;
    
}
.img-container {
    width: 8rem;
    height: 8rem;
    overflow: hidden;
    margin: 1rem;
    position: relative;
    border-radius: 50%;
    box-shadow: 0 0 5px 5px rgba(0, 0, 0, 0.5);
}

img {
  display: inline;
  margin: 0 auto;

  /*border: 2px solid yellow;*/
  height: 100%;
  width: auto;
}
</style>