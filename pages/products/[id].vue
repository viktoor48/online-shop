<template>
  <div class="container">
    <div class="flex justify-between shadow px-4 py-8 mt-6">
      <div class="product__img-big-wrapper w-3/5">
        <img class="product__big-img" :src="`${getCurrentProduct.image}`" alt="">
      </div>
      <div class="product__info w-2/5">
        <h2 class="product__title text-3xl mb-6">{{ getCurrentProduct.title }}</h2>
        <div class="product__price mb-6 text-xl">
          Цена - {{ getCurrentProduct.price }} $
        </div>
        <h3 class="text-2xl border-b mb-4">Описание продукта</h3>
        <div class="product__description mb-6">
          {{ getCurrentProduct.description }}
        </div>
        <div class="product__btn-wrapper">
          <button @click="addProductToCart(getCurrentProduct)" class="border-r-6 bg-slate-200 rounded p-2 w-full hover:bg-opacity-50">В корзину</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref, onMounted, computed} from "vue";
import { useProductStore } from "../../stores";

const store = useProductStore();

const getCurrentProduct = computed(() => {
  return store.getCurrentProduct;
})

const addProductToCart = (product) => {
  store.addToCart(product);
};

onMounted(async () => {
  const {id} = useRoute().params;
  await store.fetchCurrentProduct(id);
});
</script>

<style scoped>
.product__img-big-wrapper {
  max-height: 500px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.product__big-img {
  max-height: 100%;
}
</style>