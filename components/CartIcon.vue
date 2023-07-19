<template>
  <div class="cart-icon" :class="{'has-products': countProducts > 0}" :data-count="countProducts">
    <img src="../images/cart.svg" alt="">
  </div>
</template>

<script setup>
import {ref, computed, onMounted} from "vue";
import {useProductStore} from "../stores";

const store = useProductStore();

const countProducts = computed(() => {
  if (store.getCart) {
    let count = 0;
    store.getCart.forEach(product => {
      count = count + product.count;
    })

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
.cart-icon {
  width: 24px;
  height: 24px;
  position: relative;
}

.cart-icon.has-products::after {
  content: attr(data-count);
  display: block;
  position: absolute;
  top: -15px;
  right: -5px;
}
</style>
