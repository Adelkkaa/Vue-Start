<script setup>
import Card from './Card.vue'

const { items } = defineProps({
  items: Array
})

const onClickAdd = () => {
  alert('Добавлено в корзину')
}
</script>

<template>
  <div class="grid grid-cols-4 gap-4">
    <Card
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
      :isFavorite="false"
      :isAdded="false"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
