<template>
  <header class="bg-gray-200 p-4 flex justify-between items-center">
    <h1 class="text-2xl font-bold">Online Shop</h1>
    <div class="flex items-center">
      <CartIcon />
      <span class="ml-2 text-white">{{ cartItemsCount }} 1</span>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";
import CartIcon from "@/components/CartIcon";

const cartItemsCount = ref(0);
</script>

