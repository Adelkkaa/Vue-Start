<script setup>
import axios from 'axios'
import { onMounted, provide, reactive, ref, watch } from 'vue'

import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/Drawer.vue'

const drawerOpen = ref(false)

const items = ref([])

const filters = reactive({
  searchQuery: '',
  sortBy: 'title'
})

const fetchItems = async () => {
  try {
    const params =  {
      sortBy: filters.sortBy,
    };

    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }
    const { data } = await axios.get(
      'https://644aef902bb172ce.mokky.dev/items', {
        params
      }
    )
    items.value = data
  } catch (error) {
    console.log(error)
  }
}

onMounted(fetchItems)

watch(filters, fetchItems)

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value
}
const closeDrawer = () => {
  drawerOpen.value = false
}

const openDrawer = () => {
  drawerOpen.value = true
}

provide('cart', {
  closeDrawer,
  openDrawer
})
</script>

<template>
  <div class="w-4/5 m-auto min-h-[calc(100vh-3.5rem)] bg-white rounded-xl shadow-xl mt-14">
    <Drawer v-model:drawerOpen="drawerOpen" />
    <Header @open-drawer="openDrawer" />
    <div class="p-10 flex flex-col gap-4">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>

        <div class="flex gap-4">
          <select
            @change="onChangeSelect"
            class="py-2 px-3 border rounded-md outline-none bg-white"
          >
            <option value="name">По названию</option>
            <option value="price">По цене (дешевые)</option>
            <option value="-price">По цене (дорогие)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" />
            <input
              @input="onChangeSearchInput"
              class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400"
              type="text"
              placeholder="Поиск..."
            />
          </div>
        </div>
      </div>
      <CardList :items="items" />
    </div>
  </div>
</template>
