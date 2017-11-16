<template>
  <div class="container-cart">
    <header>
      <h1>{{ calculateNet }}</h1>
    </header>
    <div class="body-cart">
      <div class="item" :key="'cart' + item.id" v-for="item in cart">
        <img :src="item.picture"/>
        <div class="item-detail">
          <div class="text" :title="item.name">{{item.name}}</div>
          <div>
            <div>จำนวน {{item.amount}}</div>
            <div>ราคา {{item.price}} {{item.currency}}</div>
            <button @click="removeFromCart(item.id)">ลบ</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  props: ['cart', 'removeFromCart'],
  computed: {
    calculateNet () {
      const items = this.cart
      let net = 0
      const mostAmount = items.reduce((most, item) => {
        return (item.amount > most) ? item.amount : most
      }, 0)
      for (let round = 1; round <= mostAmount; round++) {
        const filterItems = items.filter((item) => {
          return item.amount >= round
        })
        const percentDiscount = (filterItems.length * 10) - 10
        net += filterItems.reduce((result, item) => {
          return result + (item.price - (item.price * (percentDiscount / 100)))
        }, 0)
      }
      return net
    }
  }
}
</script>

<style scoped>
button {
  cursor: pointer;
}

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
