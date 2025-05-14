<script setup>
import HeaderNavBar from './components/HeaderNavBar.vue'
import MainSwiper from './components/MainSwiper.vue'
import TradingViewSwiper from "@/components/TradingViewSwiper.vue";
</script>

<template>
  <header>
    <div class="wrapper">
      <HeaderNavBar msg="You did it!" />
    </div>
  </header>

  <main>
<!--    <MainSwiper />-->
    <TradingViewSwiper />
  </main>

  <footer>
    <div class="wrapper">
      <HeaderNavBar msg="You did it!" />
    </div>
  </footer>
</template>

<style scoped>

</style>