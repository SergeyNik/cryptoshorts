<script setup>
import HeaderNavBar from './components/HeaderNavBar.vue'
import MainSwiper from './components/MainSwiper.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <HeaderNavBar msg="You did it!" />
    </div>
  </header>

  <main>
    <MainSwiper />
  </main>

  <footer>
    <div class="wrapper">
      <HeaderNavBar msg="You did it!" />
    </div>
  </footer>
</template>

<style scoped>

</style>