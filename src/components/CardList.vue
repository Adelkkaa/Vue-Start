<script setup>
import Card from './Card.vue'

const onClickAdd = () => {
    alert('Добавлено в корзину')
}
</script>

<template>
  <div class="p-10">
    <h2 class="text-3xl font-bold mb-8">Все Кроссовки</h2>
    <div class="grid grid-cols-4 gap-4">
      <Card title="Мужские Кроссовки Nike Blazer Mid Suede" imageUrl="/sneakers/sneakers-1.jpg" :price="5000" :isFavorite="false" :isAdded="false" :onClickAdd="onClickAdd" />
      <Card title="Мужские Кроссовки Nike Blazer Mid Suede" imageUrl="/sneakers/sneakers-1.jpg" :price="5000" :isFavorite="true" :isAdded="false" />
      <Card title="Мужские Кроссовки Nike Blazer Mid Suede" imageUrl="/sneakers/sneakers-1.jpg" :price="5000" :isFavorite="false" :isAdded="true" />
      <Card title="Мужские Кроссовки Nike Blazer Mid Suede" imageUrl="/sneakers/sneakers-1.jpg" :price="5000" :isFavorite="true" :isAdded="true" />
    </div>
  </div>
</template>
