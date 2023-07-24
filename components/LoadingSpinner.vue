<template>
  <div class="loading">
    <div class="spinner"></div>
  </div>
</template>

<script setup>

</script>

<style>
.loading {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 130px;
}

.spinner {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  border: 4px solid #ccc;
  border-top-color: #2e475d;
  animation: spin 1s infinite linear;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
</style>

