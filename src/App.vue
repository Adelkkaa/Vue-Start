<script setup>
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue';
import { provide, ref } from 'vue';

const drawerOpen = ref(false)

const closeDrawer = () => {
  drawerOpen.value = false
}

const openDrawer = () => {
  drawerOpen.value = true
  console.log('hello')
}


provide('cart', {
  closeDrawer,
  openDrawer,
})


</script>

<template>
  <div class="w-4/5 m-auto min-h-[calc(100vh-3.5rem)] bg-white rounded-xl shadow-xl mt-14">
    <Drawer v-if="drawerOpen" />
    <Header @open-drawer="openDrawer" />
    <CardList />
  </div>
</template>
