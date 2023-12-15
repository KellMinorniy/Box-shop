<script setup>
import Card from '../components/CardShop.vue'
import { ref } from 'vue'

defineProps({
  items: Array,
  selectedCategory: String
})


</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
    />
  </div>
</template>
