<template>
  <div class="container">
    <header-bar></header-bar>
    <div class="body">
      <div class="body-left">
        <div class="promotion-container">
          <div>Promotion</div>
          <div>
            Naidin Book Center ออกโปรโมชั่นสำหรับหนังสือ Harry Potter ทั้ง 7 ภาค โดยเมื่อ..
          </div>
          <div>
            <div>ซื้อเล่มไม่ซ้ำกัน 2 เล่ม ลด 10% ของ 2 เล่มนั้น</div>
            <div>ซื้อเล่มไม่ซ้ำกัน 3 เล่ม ลด 20% ของ 3 เล่มนั้น</div>
            <div>ซื้อเล่มไม่ซ้ำกัน 4 เล่ม ลด 30% ของ 4 เล่มนั้น</div>
            <div>ซื้อเล่มไม่ซ้ำกัน 5 เล่ม ลด 40% ของ 5 เล่มนั้น</div>
            <div>ซื้อเล่มไม่ซ้ำกัน 6 เล่ม ลด 50% ของ 6 เล่มนั้น</div>
            <div>ซื้อเล่มไม่ซ้ำกัน 7 เล่ม ลด 60% ของ 7 เล่มนั้น</div>
          </div>
        </div>
        <div class="product-container">
          <div :key="product.id" v-for="product in products" class="card">
            <product-item
              :product="product"
              :addToCart="addToCart"/>
          </div>
        </div>
      </div>
      <div class="body-right">
        <cart
          :cart="cart"
          :removeFromCart="removeFromCart"/>
      </div>
    </div>
  </div>
</template>

<script>
import Cart from '@/components/Cart.vue'
import Header from '@/components/Header.vue'
import ProductItem from '@/components/ProductItem.vue'

export default {
  components: {
    'cart': Cart,
    'header-bar': Header,
    'product-item': ProductItem
  },
  data () {
    return {
      products: [
        {id: 1, name: `Harry Potter and the Philosopher's Stone`, price: 100, currency: 'บาท', picture: 'static/pictures/HarryBook1.jpg'},
        {id: 2, name: `Harry Potter and the Chamber of Secrets`, price: 100, currency: 'บาท', picture: 'static/pictures/HarryBook2.jpg'},
        {id: 3, name: `Harry Potter and the Prisoner of Azkaban`, price: 100, currency: 'บาท', picture: 'static/pictures/HarryBook3.jpg'},
        {id: 4, name: `Harry Potter and the Goblet of Fire`, price: 100, currency: 'บาท', picture: 'static/pictures/HarryBook4.jpg'},
        {id: 5, name: `Harry Potter and the Order of the Phoenix`, price: 100, currency: 'บาท', picture: 'static/pictures/HarryBook5.jpg'},
        {id: 6, name: `Harry Potter and the Half-Blood Prince`, price: 100, currency: 'บาท', picture: 'static/pictures/HarryBook6.jpg'},
        {id: 7, name: `Harry Potter and the Deathly Hallows`, price: 100, currency: 'บาท', picture: 'static/pictures/HarryBook7.jpg'}
      ],
      cart: []
    }
  },
  methods: {
    addToCart (newItem) {
      let cartItem = this.cart.find((item) => {
        return item.id === newItem.id
      })

      if (cartItem) {
        this.cart = this.cart.map((product) => {
          return (product.id === newItem.id)
          ? {...product, amount: product.amount + 1}
          : product
        })
      } else {
        this.cart = [
          ...this.cart,
          {...newItem, amount: 1}
        ]
      }
    },
    removeFromCart (itemId) {
      this.cart = this.cart.filter((item) => {
        return item.id !== itemId
      })
    }
  }
}
</script>

<style scoped>
.body {
  display: flex;
  height: calc(100vh - 95px);
}

.body-left {
  height: 100%;
  margin-right: 10px;
  overflow: scroll;
  width: 70%;
}

.body-right {
  height: 100%;
  width: 30%;
}

.card {
  margin: 25px 0px;
  padding: 10px;
  width: 25%;
}

.container {
  background: #F1F1F1;
  height: 100vh;
  width: 100vw;
}

.product-container {
  background: #FFFFFF;
  display: flex;
  flex-wrap: wrap;
  width: 100%;
}

.promotion-container {
  background: #FFFFFF;
  width: 100%;
}
</style>
