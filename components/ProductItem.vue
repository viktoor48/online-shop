<template>
  <div class="product border rounded p-4 flex flex-col">
    <div class="product__img-container mb-4">
      <img :src="props.product.image" alt="" class="product__img">
    </div>
    <div class="product__information mt-auto">
      <div class="product__info-head">
        <NuxtLink class="mb-4 block" :to="`/products/${props.product.id}`">
          <h3 class="font-bold">{{ props.product.title }}</h3>
        </NuxtLink>
        <p class="mb-2">Цена: {{props.product.price}} $</p>
      </div>
      <div class="product__info-footer">
        <button @click="addProductToCart(props.product)" class="border-r-6 bg-slate-200 rounded p-2 w-full hover:bg-opacity-50">В Корзину</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import {useProductStore} from "../stores";

const store = useProductStore();
const props = defineProps({
  product: {
    type: Object,
    required: true,
  }
});

const addProductToCart = (product) => {
  console.log(product.id);
  store.addToCart(product);
};
</script>

<style scoped>
.product__img-container {
  height: 300px;
  display: flex;
}

.product__img {
  object-fit: cover;
  max-width: 100%;
  max-height: 100%;
  margin: auto;
}
</style>
