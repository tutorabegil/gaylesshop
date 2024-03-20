<template>
  <div class="main">
    <div class="app-container" style="background-image: url('/img/logo.png'); background-size: cover; height: 150vh; display: flex;">
    <ProductList @add-to-cart="addToCart"></ProductList>
    <ShoppingCart :cartItems="cartItems" @remove-from-cart="removeFromCart"></ShoppingCart>
  </div>
  </div>
</template>

<script>
// Importing components
import ProductList from './components/ProductList.vue';
import ShoppingCart from './components/ShoppingCart.vue';

export default {
  components: {
    ProductList, // Registering the ProductList component
    ShoppingCart // Registering the ShoppingCart component
  },
  // Data function to initialize data properties
  data() {
    return {
      cartItems: [] // Array to hold items added to the shopping cart
    };
  },
  // Methods for adding and removing items from the shopping cart
  methods: {
    addToCart(product) {
      // Check if the product is already in the cart
      const existingItem = this.cartItems.find(item => item.id === product.id);
      if (existingItem) {
        // If the product is already in the cart, increase its quantity
        existingItem.quantity++;
      } else {
        // If the product is not in the cart, add it with a quantity of 1
        this.cartItems.push({ ...product, quantity: 1 });
      }
    },
    removeFromCart(item) {
      // Find the index of the item in the cart
      const index = this.cartItems.findIndex(cartItem => cartItem.id === item.id);
      if (index !== -1) {
        // If the item is found, remove it from the cart
        this.cartItems.splice(index, 1);
      }
    }
  }
};
</script>

<style scoped>
body{
  background: green;

}
.app-container {
  display: flex;
  justify-content: space-around;
  align-items: flex-start;
  padding: 10px;
  background-color: green;

 
}
</style>
