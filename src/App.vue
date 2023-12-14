<script setup>
import { onMounted } from 'vue';
import axios from 'axios';
import { ref } from 'vue'

import HeaderShop from './components/HeaderShop.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/DrawerShop.vue'

const items = ref([])

onMounted(async () => {
  try {
    const {data} = await axios.get('https://604781a0efa572c1.mokky.dev/items')
    console.log(data)
    
    items.value = data;
  } catch (e) {
    console.log(err)
  }
})
</script>

<template>
    <!-- <Drawer /> -->


  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14 ">
    <HeaderShop />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold text-slate-700 mb-8">Все товары:</h2>

        <div class="flex gap-4">
          <select name="" id="" class="py-2 px-3 border rounded-md outline-none">
            <option value="">По названию</option>
            <option value="">Сначала дешевые</option>
            <option value="">Сначала дорогие</option>
            <option value="">Все</option>
          </select>

          <div class="relative">
            <img src="/search.svg" alt="" class="absolute left-3 top-3" />
            <input
              type="text"
              placeholder="Поиск..."
              class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400"
            />
          </div>
        </div>
      </div>
      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
