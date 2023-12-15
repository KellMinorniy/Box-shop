<script setup>
import { onMounted } from 'vue'
import axios from 'axios'
import { ref } from 'vue'

import HeaderShop from './components/HeaderShop.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/DrawerShop.vue'
import HeaderText from './components/HeaderText.vue'

const items = ref([])
const selectedFilter = ref('Все') // переменная для хранения текущего выбранного фильтра
const selectedCategory = ref('Все') // переменная для хранения текущей выбранной категории

onMounted(async () => {
  try {
    const { data } = await axios.get('https://604781a0efa572c1.mokky.dev/items')
    console.log(data)

    items.value = data
  } catch (e) {
    console.log(err)
  }
})

const filterByCategory = () => {
  // функция для фильтрации по категории
  let filteredItems = [...items.value]

  if (selectedCategory.value !== 'Все') {
    filteredItems = filteredItems.filter((item) => item.category === selectedCategory.value)
  }

  items.value = filteredItems
}

const sortByFilter = () => {
  // функция для сортировки по выбранному фильтру
  let sortedItems = [...items.value]

  switch (selectedFilter.value) {
    case 'По названию':
      sortedItems.sort((a, b) => a.title.localeCompare(b.title))
      break
    case 'Сначала дешевые':
      sortedItems.sort((a, b) => a.price - b.price)
      break
    case 'Сначала дорогие':
      sortedItems.sort((a, b) => b.price - a.price)
      break
  }

  items.value = sortedItems
}
</script>

<template>
  <!-- <Drawer /> -->
  <div class="w-full">
    <!-- <HeaderText /> -->
    <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-9">
      <HeaderShop />
      <div class="p-10">
        <div class="flex justify-between items-center">
          <h2 class="text-3xl font-bold text-slate-700 mb-8">Все товары:</h2>

          <div class="flex gap-4">
            <select
              v-model="selectedCategory"
              @change="filterByCategory"
              class="py-2 px-3 border rounded-md outline-none"
            >
              <option value="Обувь">Обувь</option>
              <option value="Худи/Свитшоты">Худи/Свитшоты</option>
              <option value="Джинсы">Джинсы</option>
              <option value="Спортивная одежда">Спортивная одежда</option>
              <option value="Все">Все</option>
            </select>

            <select
              v-model="selectedFilter"
              @change="sortByFilter"
              class="py-2 px-3 border rounded-md outline-none"
            >
              <option value="По названию">По названию</option>
              <option value="Сначала дешевые">Сначала дешевые</option>
              <option value="Сначала дорогие">Сначала дорогие</option>
              <option value="Все">Все</option>
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
  </div>
</template>

<style scoped></style>
