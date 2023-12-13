<script setup>

    defineProps({
        imageUrl: String,
        title: String,
        price: Number,
        isFavorite: Boolean,
        isAdded: Boolean,
        onClickAdd: Function,
        onClickFavorite: Function
    })


</script>

<template>
    <div class="relative border-slate-700 bg-white rounded-3xl p-8 cursor-pointer hover:-translate-y-2 hover:shadow-xl transition">
      <img @click="onClickFavorite" :src="!isFavorite ? '/like-2.svg' : '/like-1.svg'" alt="Like 2" class="absolute top-8 left-8">
      <img :src="imageUrl" alt="Item" />
      <p class="mt-2">{{ title }}</p>

      <div class="flex justify-between">
        <div class="flex flex-col mt-5">
          <span class="text-slate-600">Цена:</span>
          <b>{{ price }}</b>
        </div>
        <img @click="onClickAdd" :src="!isAdded ? '/plus.svg': '/checked.svg'" alt="add" />
      </div>
    </div>
</template>