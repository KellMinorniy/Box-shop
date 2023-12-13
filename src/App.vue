<script setup>
import HeaderShop from "./components/HeaderShop.vue"
import CardList from "./components/CardList.vue"
import Drawer from "./components/DrawerShop.vue";

</script>

<template>
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Drawer />
    <HeaderShop />

    <div class="p-10">
      <h2 class="text-3xl font-bold text-slate-700 mb-8">Все товары:</h2>

      <CardList />
    </div>
    
  </div>
</template>

<style scoped>

</style>