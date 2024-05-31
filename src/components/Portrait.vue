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
        <div>
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

img {
  border-radius: 50%;
  /*border: 2px solid yellow;*/
  box-shadow: 0 0 5px 5px rgba(0, 0, 0, 0.5);
  margin: 1rem;
}
</style>