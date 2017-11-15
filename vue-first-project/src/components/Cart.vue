<template>
  <div class="container-cart">
    <header>
      <h1>{{ sumNet }}</h1>
    </header>
    <div class="body-cart">
      <div class="item" :key="'cart' + item.id" v-for="item in cart">
        <img />
        <div class="item-detail">
          <div class="text" :title="item.name">{{item.name}}</div>
          <div>
            <div>จำนวน {{item.amount}}</div>
            <div>ราคา {{item.price}} {{item.currency}}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  props: ['cart'],
  computed: {
    sumNet () {
      return this.cart.reduce((sum, item) => {
        return sum + (item.price * item.amount)
      }, 0)
    }
  }
}
</script>

<style scoped>
header {
  align-items: center;
  background: #1480E2;
  color: #FFF;
  display: flex;
  height: 75px;
  justify-content: flex-end;
  padding: 0px 25px;
}

img {
  background: #FCFCFC;
  height: 100px;
  margin-right: 10px;
  width: 100px;
}

.body-cart {
  height: calc(100% - 75px);
  overflow: scroll;
}

.container-cart {
  background: #FFFFFF;
  width: 100%;
  height: 100%;
}

.item {
  display: flex;
  padding: 10px;
}

.item-detail {
  width: calc(100% - 110px)
}

.text {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>
