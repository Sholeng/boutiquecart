<template>
  <div class="shopping-cart">
    <h2>Shopping Cart</h2>
    <ul>
      <li v-for="item in cart" :key="item.id">
        <div>{{ item.name }}</div>
        <div>
          ₱{{ item.price }} - Quantity:
          <input type="number" v-model.number="item.quantity" @change="updateQuantity(item.id, item.quantity)">
          <button @click="removeFromCart(item.id)" style="color: rgba(0, 128, 0, 0.8);
          background-color: rgba(0, 128, 0, 0.5);" class="removeFromCart">Remove</button>
        </div>
      </li>
    </ul>
    <div>Total: ₱{{ totalPrice }}</div>
  </div>
</template>

<script>
export default {
  name: 'ShoppingCart',
  props: {
    cart: {
      type: Array,
      required: true
    }
  },
  computed: {
    totalPrice() {
      return this.cart.reduce((total, item) => total + item.price * item.quantity, 0);
    }
  },
  methods: {
    updateQuantity(productId, quantity) {
      this.$emit('update-quantity', { productId, quantity: parseInt(quantity) });
    },
    removeFromCart(productId) {
      this.$emit('remove-from-cart', productId);
    }
  }
};
</script>
