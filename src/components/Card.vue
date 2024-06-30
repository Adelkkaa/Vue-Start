<script setup>
defineProps({
  title: String,
  imageUrl: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onClickFavorite: Function
})
</script>

<template>
  <div class="bg-white relative border border-slate-300 rounded-3xl p-8 cursor-pointer">
    <img
      class="absolute top-8 left-8"
      :src="isFavorite ? '/like-2.svg' : '/like-1.svg'"
      alt="card"
    />
    <img :src="imageUrl" alt="card" />
    <p class="text-sm">{{ title }}</p>
    <div class="flex items-center justify-between">
      <div>
        <span class="text-xs font-medium text-gray-500">Цена:</span>
        <p class="text-sm font-bold">{{ price }} руб.</p>
      </div>
      <img @click="onClickAdd" :src="isAdded ? '/checked.svg' : '/plus.svg'" alt="plus" />
    </div>
  </div>
</template>
