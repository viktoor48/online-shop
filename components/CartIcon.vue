<template>
  <div class="w-[24px] h-[24px] relative" :class="{'has-products': countProducts > 0}" :data-count="countProducts">
    <img src="../images/cart.svg" alt="">
  </div>
</template>

<script setup>
import {computed, onMounted} from "vue";
import {useProductStore} from "../stores";

const store = useProductStore();

const countProducts = computed(() => {
  if (store.getCart) {
    let count = 0;
    // store.getCart.forEach(product => {
    //   count = count + product.count;
    // })
    count = store.getCart.length;

    return count;
  } else {
    return 0;
  }
})

const getCartFromStorage = () => {
  const cart = localStorage.getItem('cart');

  if (cart === null) {
    return [];
  }

  try {
    return JSON.parse(cart);
  } catch (e) {
    localStorage.removeItem('cart')
    return [];
  }
};

onMounted( () => {
  const cart = getCartFromStorage();
  store.updateCart(cart);
});
</script>

<style scoped>

.has-products::after {
  content: attr(data-count);
  @apply top-[-15px] right-[-5px] absolute block
}

</style>
