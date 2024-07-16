<script setup>
import { computed, provide, ref, watch } from 'vue'

import Header from './components/Header.vue'
import Drawer from './components/Drawer.vue'

const drawerOpen = ref(false)

const totalPrice = computed(() => cart.value.reduce((acc, item) => acc + item.price, 0))
const vatPrice = computed(() => Math.round((totalPrice.value * 5) / 100))

const cart = ref([])

const addToCart = (item) => {
  console.log('first')
  cart.value.push(item)
  item.isAdded = true
}

const removeFromCart = (item) => {
  cart.value.splice(cart.value.indexOf(item), 1)
  item.isAdded = false
}

const closeDrawer = () => {
  drawerOpen.value = false
}

const openDrawer = () => {
  drawerOpen.value = true
}

watch(
  cart,
  () => {
    localStorage.setItem('cart', JSON.stringify(cart.value))
  },
  { deep: true }
)



provide('cart', {
  closeDrawer,
  openDrawer,
  addToCart,
  cart,
  removeFromCart
})
</script>

<template>
  <div class="w-4/5 m-auto min-h-[calc(100vh-3.5rem)] bg-white rounded-xl shadow-xl mt-14">
    <Drawer v-model:drawerOpen="drawerOpen" :total-price="totalPrice" :vat-price="vatPrice" />
    <Header @open-drawer="openDrawer" />
    <div class="p-10">
      <router-view></router-view>
    </div>
  </div>
</template>
