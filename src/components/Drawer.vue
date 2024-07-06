<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue'
import { inject, ref } from 'vue'

const buttonDisabled = ref(false)
defineProps({
  drawerOpen: Boolean
})

const { closeDrawer } = inject('cart')

</script>

<template>
  <Transition
    enter-active-class="duration-300 ease-out"
    enter-from-class="transform opacity-0"
    enter-to-class="opacity-100"
    leave-active-class="duration-200 ease-in"
    leave-from-class="opacity-100"
    leave-to-class="transform opacity-0"
  >
    <div
      @click="closeDrawer"
      v-show="drawerOpen"
      class="absolute block left-0 top-0 w-full h-full bg-black bg-opacity-50 z-10"
      :class="{ hidden: !drawerOpen }"
    ></div>
  </Transition>
  <Transition
    enter-active-class="duration-300 ease-in-out"
    enter-from-class="translate-x-full"
    enter-to-class="translate-x-0"
    leave-active-class="duration-200 ease-in"
    leave-from-class="translate-x-0"
    leave-to-class="translate-x-full"
  >
    <div
      v-show="drawerOpen"
      class="fixed right-0 top-0 w-96 h-full bg-white p-8 transition-transform z-20"
    >
      <DrawerHead />
      <CartItemList />
      <div class="flex flex-col gap-4 mt-7">
        <div class="flex gap-2">
          <span>Итого:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>12900 ₽</b>
        </div>

        <div class="flex gap-2">
          <span>Налог 5%:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>900 ₽</b>
        </div>

        <button
          :disabled="buttonDisabled"
          class="mt-4 transition bg-lime-500 w-full rounded-xl py-3 text-white disabled:bg-slate-300 hover:bg-lime-600 active:bg-lime-700 cursor-pointer"
        >
          Оформить заказ
        </button>
      </div>
    </div></Transition
  >
</template>
