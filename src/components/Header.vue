<script setup>
const emit = defineEmits(['openDrawer'])
</script>

<template>
  <header class="flex p-11 justify-between items-center border-slate-300 border-b">
    <router-link to="/"
      ><div class="flex items-start gap-4">
        <img class="w-10 h-10 rounded-full" src="logo.png" alt="logo" />
        <div class="flex flex-col">
          <h1 class="font-bold text-xl leading-6 uppercase">Vue Sneakers</h1>
          <p class="font-regular text-sm text-gray-500">Магазин лучших кроссовок</p>
        </div>
      </div></router-link
    >
    <nav>
      <ul class="flex gap-8">
        <li
          @click="() => emit('openDrawer')"
          class="flex gap-2.5 items-center text-gray-500 hover:text-black cursor-pointer"
        >
          <img src="cart.svg" alt="cart" />
          <p class="font-semibold text-sm">Корзина</p>
        </li>
        <router-link to="/favorites">
          <li class="flex gap-2.5 items-center text-gray-500 hover:text-black cursor-pointer">
            <img src="heart.svg" alt="cart" />
            <p class="font-semibold text-sm">Закладки</p>
          </li></router-link
        >
        <li class="flex gap-2.5 items-center text-gray-500 hover:text-black cursor-pointer">
          <img src="profile.svg" alt="cart" />
          <p class="font-semibold text-sm">Профиль</p>
        </li>
      </ul>
    </nav>
  </header>
</template>
