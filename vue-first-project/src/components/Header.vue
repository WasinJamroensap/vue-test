<template>
  <header>
    <h1 class="header-storename">Naidin Book Store</h1>
    <div class="header-choice">
      <h2>Home</h2>
      <h2>Checkout</h2>
    </div>
  </header>
</template>

<script></script>

<style scoped>
header {
  align-items: center;
  display: flex;
  flex-direction: row;
  height: 75px;
  justify-content: center;
  width: 100%;
}

.header-choice {
  display: flex;
}

.header-choice > h2 {
  cursor: pointer;
  margin: 0px 20px;
}

.header-choice > h2:hover {
  text-decoration: underline;
}

.header-storename{
  position: absolute;
  left: 50px;
}
</style>
