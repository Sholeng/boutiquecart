<template>
  <div id="app">
    <ProductList @add-to-cart="addToCart" />
    <ShoppingCart :cart="cart" @update-quantity="updateQuantity" @remove-from-cart="removeFromCart" />
  </div>
</template>

<script>
import ShoppingCart from './components/ShoppingCart.vue';
import ProductList from './components/ProductList.vue';

export default {
  name: 'App',
  components: {
    ShoppingCart,
    ProductList
  },
  data() {
    return {
      cart: []
    };
  },
  methods: {
    addToCart(product) {
      const existingItem = this.cart.find(item => item.id === product.id);
      if (existingItem) {
        existingItem.quantity++;
      } else {
        this.cart.push({ ...product, quantity: 1 });
      }
    },
    updateQuantity(payload) {
      const { productId, quantity } = payload;
      const item = this.cart.find(item => item.id === productId);
      if (item) {
        item.quantity = quantity;
      }
    },
    removeFromCart(productId) {
      this.cart = this.cart.filter(item => item.id !== productId);
    }
  }
};
</script>
