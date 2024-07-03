<script setup>
import CartItem from './CartItem.vue'
const cart = Array.from({length: 5}, (_, i) => ({id: i, price: 12900, imageUrl: '/sneakers/sneakers-1.jpg', title: 'Мужские Кроссовки Nike Blazer Mid Suede'}))

</script>

<template>
  <div class="flex flex-col flex-1 gap-4 justify-between" v-auto-animate>
    <CartItem
      v-for="item in cart"
      :key="item.id"
      :title="item.title"
      :price="item.price"
      :image-url="item.imageUrl"
    />
  </div>
</template>
