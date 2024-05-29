<script setup>
import { ref } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import Portrait from './components/Portrait.vue'

const users = ref([
  { name: 'Diem Bang', contact:'diem@mail.com' },
  { name: 'Bosse Pettersson Bang', contact:'bosse@mail.com' },
  { name: 'Jakob Pettersson', contact:'jakob@mail.com' }
  ])
</script>

<template>
  
<HelloWorld msg="Our Team" />
  <div v-for="user in users">
    <Portrait :name="user.name" :contact="user.contact" />
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
