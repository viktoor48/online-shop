<template>
  <div class="wrapper">
    <header class="header bg-[#213343] p-4">
      <div class="container">
        <div class="header__row">
          <nav class="header__menu flex justify-between">
            <div class="header__logo">
              <NuxtLink to="/" class="text-2xl">
                Online Shop
              </NuxtLink>
            </div>
            <ul class="flex">
              <li class="header__menu-link"><NuxtLink to="/catalogProducts">Каталог</NuxtLink></li>
              <li class="header__menu-link header__link-cart"><NuxtLink class="cart-link" to="/cartPage">Корзина</NuxtLink><CartIcon/></li>
            </ul>
          </nav>
        </div>
      </div>
    </header>
    <main class="main p-4">
      <slot/>
    </main>
    <footer class="footer bg-[#213343] p-4">
      <div class="container">
        <div class="text-blue text-center">
          Copyright © 2023 HubSpot, Inc.
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
}

.main {
  display: flex;
  flex: 1 1 auto;
}

.footer {
  width: 100%;
}

.container {
  max-width: 1120px;
  margin: 0 auto;
}

.main {
  color: #2e475d;
}

.header__menu-link {
  cursor: pointer;
}

.header__menu-link + .header__menu-link {
  margin-left: 20px;
}

.cart-link {
  margin-right: 4px;
}

.header__link-cart {
  display: flex;
}

.router-link-exact-active {
  color: #69dae8;
}
</style>