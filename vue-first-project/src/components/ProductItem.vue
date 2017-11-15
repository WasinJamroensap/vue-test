<template>
  <div class="contianer">
    <img src="https://naidin-da010.firebaseapp.com/static/imgs/1.jpg" />
    <div>
      <div>
        <div class="text">{{ product.name }}</div>
        <hr/>
        <div class="text">{{ product.price }} {{ product.currency }}</div>
      </div>
      <button class="text" @click="addToCart(product)">Add to cart</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['addToCart', 'product']
}
</script>

<style scoped>
button {
  background: #1480E2;
  border: 1px solid #1480E2;
  color: #FFF;
  cursor: pointer;
  height: 50px;
  width: 100%;
}

.contianer {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,.2), 0 6px 20px 0 rgba(0,0,0,.19);
  height: 100%;
  width: 100%;
}

.contianer > img {
  height: calc(100% - 100px);
  width: 100%;
}

.text {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>
