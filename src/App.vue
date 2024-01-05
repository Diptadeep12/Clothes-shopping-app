<template>
   <h1 class="page-title">Elegant Garments</h1>
  <div id="app">
    <product-list :products="products" @add-to-cart="addToCart" />
    <div>
      <h2>Shopping Cart</h2>
      <cart-item v-for="item in cart" :key="item.id" :item="item" @remove-from-cart="removeFromCart" />
    </div>
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';
import CartItem from './components/CartItem.vue';

export default {
  components: {
    ProductList,
    CartItem,
  },
  data() {
    return {
      products: [], // Fetch products from API or provide a static list
      cart: [],
    };
  },
  methods: {
    addToCart(product) {
      const existingItem = this.cart.find((item) => item.id === product.id);

      if (existingItem) {
        existingItem.quantity++;
      } else {
        this.cart.push({ ...product, quantity: 1 });
      }
    },
    removeFromCart(item) {
      const index = this.cart.findIndex((cartItem) => cartItem.id === item.id);

      if (index !== -1) {
        this.cart.splice(index, 1);
      }
    },
  },
  mounted() {
  // Provide static products with English descriptions and actual image paths
  const staticProducts = [
    {
      id: 1,
      title: 't-shirt',
      body: 'US Polo cotton blend t shirt for men',
      price: '$19.99',
      image: '/images/product1.jpg', // Update with the actual image path
    },
    {
      id: 2,
      title: 'Full Sleeve Shirt',
      body: 'Levi full sleeve shirt for men',
      price: '$29.99',
      image: '/images/product2.jpg', // Update with the actual image path
    },
    {
      id: 3,
      title: 'Sweater',
      body: 'Oswal Sweater for men',
      price: '$39.99',
      image: '/images/product3.jpg', // Update with the actual image path
    },
    {
      id: 4,
      title: 'Blue Jeans',
      body: 'Blue Pepe jeans pants for men',
      price: '$24.99',
      image: '/images/product4.jpg', // Update with the actual image path
    },
    {
      id: 5,
      title: 'Formal Shirt',
      body: 'Peter England Pink colored Cotton Blend Formal Shirt for men',
      price: '$14.99',
      image: '/images/product5.jpg', // Update with the actual image path
    },
    {
      id: 6,
      title: 'Formal Footwear',
      body: 'Woodland Black Formal Shoe for men',
      price: '$23.99',
      image: '/images/product6.jpg', // Update with the actual image path
    },
    // Add more products as needed
  ];

  this.products = staticProducts;
}

};
</script>

<style>
/* Global Styles */
body {
  font-family: 'Arial', sans-serif;
  margin: 0;
  padding: 0;
  background-image: url('/public/images/bg1.jpg');
;
 /* Update with your background image path */
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

h2 {
  color: #333;
}

/* Add more global styles as needed */
</style>

