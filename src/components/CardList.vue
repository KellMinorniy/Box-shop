<script setup>
import Card from "../components/CardShop.vue"

const onClickAdd = () => {
    alert('Товар успешно добавлен')
}
</script>

<template>
    <div class="grid grid-cols-4 gap-5">
        <Card
         title="Кроссовки Nike" 
         image-url="/sneakers/sneakers-1.jpg" 
         :price="4000" :is-added="false" 
         :is-favorite="false" 
         :onClickAdd="onClickAdd()"
         />
         
         
        <Card title="Кроссовки Nike 2" image-url="/sneakers/sneakers-2.jpg" :price="5000"/>
        <Card title="Кроссовки Nike 3" image-url="/sneakers/sneakers-3.jpg" :price="10000"/>
        <Card title="Кроссовки Nike 4" image-url="/sneakers/sneakers-4.jpg" :price="4130"/>
        <Card title="Кроссовки Nike 5" image-url="/sneakers/sneakers-5.jpg" :price="6000"/>
    </div>
</template>