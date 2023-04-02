<template>
  <div class="cart">
    <h1>This is an about page</h1>
    <div class="cart">
  <h1>{{cart.length}} in cart</h1>
  <Cart class="carty"
  v-for="(product, index) in cart"
  @removeItemFromCart="removeItemFromCart(product)" 
 :key="index"
 :image="product.img"
 :title="product.name"
 :quantity="product.quantity"
 :cost="product.cost"/>
 <p> </p>
</div>
  </div>
</template>
<script>
import Cart from '../components/Cart.vue';
export default {
  name: 'Home',
  components: {
    Cart
  },

  
}
</script>


