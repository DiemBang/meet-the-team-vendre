<script setup>
import { ref } from 'vue'

defineProps({
  name: String,
  contact: String,
  img: String
})

// const count = ref(0)
</script>

<template>
    <section class="portrait">
        <div class="name">{{ name }}</div>
        <div class="contact"><a :href="`mailto:${contact}`">Contact me</a></div>
        <div>
            <img :src="img" alt="Photo of the team member">
        </div>
        
    </section>
</template>