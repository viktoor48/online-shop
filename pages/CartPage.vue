<template>
  <div class="container">
    <div class="cart-wrapper">
      <div v-for="cart in getCart" :key="cart.id" class="cart-item flex justify-between py-4">
        <div class="cart-item__img w-1/4">
          <img :src="cart.image" alt="">
        </div>
        <div class="cart-item__info w-2/4 flex-col justify-between flex">
          <div>
            <div class="cart-item__title mb-2">{{cart.title}}</div>
            <div class="cart-item__category">
              Категория: {{ cart.category }}
            </div>
          </div>
          <div>
            <button @click="removeProduct(cart)" class="p-2">Удалить</button>
          </div>
        </div>
        <div class="cart-item__action flex flex-col justify-between w-1/4">
          <div class="cart-item__price text-xl">
            {{ cart.price }}$
          </div>
          <div class="cart-item__count flex justify-between">
            <div @click="minesProduct(cart)" class="text-2xl cursor-pointer" :class="{'text-gray-300': cart.count == 1}">-</div>
            <div class="text-2xl">{{ cart.count }}</div>
            <div @click="addProduct(cart)" class="text-2xl cursor-pointer">+</div>
          </div>
        </div>
      </div>
      <div class="cart__total-price text-2xl my-6 ml-5">
        Итого: {{getTotalPrice}}$
      </div>
    </div>
  </div>
</template>

<script setup>
import {useProductStore} from "../stores";
import {computed, onMounted} from "vue";

const store = useProductStore();

const getCart = computed(() => {
  return store.getCart;
});

const getTotalPrice = computed(() => {
  let price = 0;
  getCart.value.forEach(product => {
    price += product.count * product.price;
  });

  return price;
});

const addProduct = (product) => {
  store.addToCart(product);
};

const minesProduct = (product) => {
  if (product.count > 1) {
    store.minesFromCart(product);
  }
};

const removeProduct = (product) => {
  store.removeFromCart(product);
};
</script>

<style scoped>
.cart-item__img {
  height: 156px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.cart-item__img img {
  object-fit: cover;
  max-height: 100%;
  max-width: 100%;
}

.cart-item + .cart-item {
  border-top: 1px solid #2e475d;
}
</style>