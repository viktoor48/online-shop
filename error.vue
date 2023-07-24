<template>
  <div class="h-screen mx-auto text-center text-black flex justify-center items-center flex-col">
    <p class="text-7xl font-bold">{{ error.statusCode }}</p>
    <p class="mt-7 text-6xl">Ooops.</p>
    <p class="mt-7">{{ error.message }}</p>
  </div>
</template>

<script setup>
const props = defineProps(['error']);
console.log(props.error);
</script>

<style scoped>

</style>