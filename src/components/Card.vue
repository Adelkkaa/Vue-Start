<script setup>
defineProps({
  id: Number,
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
  <div
    class="bg-white relative border border-slate-300 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl"
  >
    <img
      v-if="onClickFavorite"
      @click="onClickFavorite"
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
      <img v-if="onClickAdd" @click="onClickAdd" :src="isAdded ? '/checked.svg' : '/plus.svg'" alt="plus" />
    </div>
  </div>
</template>
