<template>
    <div class="product-list">
      <div class="column">
        <div v-for="(product, index) in products.slice(0, 5)" :key="index">
          <h3>{{ product.name }}</h3>
          <p>Price: {{ product.price }}</p>
          <button @click="addToCart(product)" style="color: rgba(0, 128, 0, 0.8);
           background-color: rgba(0, 128, 0, 0.5);" class="addToCart">Add to Cart</button>
        </div>
      </div>
      <div class="column">
        <div v-for="(product, index) in products.slice(5)" :key="index">
          <h3>{{ product.name }}</h3>
          <p>Price: {{ product.price }}</p>
          <button @click="addToCart(product)" 
          style="color: rgba(0, 128, 0, 0.8); 
          background-color: rgba(0, 128, 0, 0.5);" class="addToCart">Add to Cart</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProductList',
    data() {
      return {
        products: [
          { id: 1, name: 'T-Shirt', price: 150 },
          { id: 2, name: 'Dress', price: 200 },
          { id: 3, name: 'Pants', price: 300 },
          { id: 4, name: 'Crop top', price: 180 },
          { id: 5, name: 'Polo Shirt', price: 200 },
          { id: 6, name: 'Denim Pants', price: 280 },
          { id: 7, name: 'Formal Dress', price: 300 },
          { id: 8, name: 'V Neck Shirt', price: 150 },
          { id: 9, name: 'Hoodie T-Shirt', price: 300 },
          { id: 10, name: 'Long Sleeve', price: 250 },
          // Add more products as needed
        ]
      };
    },
    methods: {
      addToCart(product) {
        this.$emit('add-to-cart', product);
      }
    }
  };
  </script>
  
  <style scoped>
  .product-list {
    display: flex;
  }
  
  .column {
    flex: 1;
  }
  
  .column:not(:last-child) {
    margin-right: 0px;
  }

  button {
  margin-bottom: 0px;
}

.product.price {
    display: flex;
  }

  button {
  margin-bottom: 0px;
}

  </style>
  