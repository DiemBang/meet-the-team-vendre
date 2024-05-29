<script setup>
import { ref } from 'vue'

defineProps({
  name: String,
  contact: String
})

// const count = ref(0)
</script>

<template>
    <section class="portrait">
        <div class="name">{{ name }}</div>
        <div class="contact"><a :href="`mailto:${contact}`">Contact me</a></div>
    </section>
</template>