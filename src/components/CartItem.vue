<template>
    <div class="cart-item">
      <h3>{{ item.name }}</h3>
      <p>Price: {{ item.price }}</p>
      <p>Quantity: {{ item.quantity }}</p>
      <button @click="removeFromCart">Remove from Cart</button>
    </div>
  </template>
  
  <script>
  export default {
    props: ['item'],
    methods: {
      removeFromCart() {
        this.$emit('remove-from-cart', this.item);
      },
    },
  };
  </script>
  
  <style scoped>
  .cart-item {
    border: 1px solid #ddd;
    padding: 15px;
    margin: 10px;
    text-align: center;
    background-color: #f9f9f9;
  }
  
  .cart-item h3 {
    margin-bottom: 5px;
  }
  
  .cart-item p {
    margin: 5px 0;
  }
  
  .cart-item button {
    background-color: #e53935;
    color: #fff;
    padding: 8px 16px;
    border: none;
    cursor: pointer;
  }
  
  .cart-item button:hover {
    background-color: #c62828;
  }
  </style>
  