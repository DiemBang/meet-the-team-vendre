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
        <div class="name">{{ firstName + ' ' + lastName }}</div>
        <div class="contact"><a :href="`mailto:${contact}`">Contact me</a></div>
        <div>
            <img :src="img" alt="Photo of the team member">
        </div>
        
    </section>
</template>