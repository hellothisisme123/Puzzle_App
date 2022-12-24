<script setup lang="ts">
// import HelloWorld from './components/HelloWorld.vue'
  import navbar from './components/navBar.vue'
  import puzz_board from './components/puzz_board.vue'
</script>

<template>
  <div>
    <navbar></navbar>    
    <puzz_board pieces="30"></puzz_board>
  </div>
  <!-- <HelloWorld msg="Vite + Vue" /> -->
</template>

<style scoped>

</style>
