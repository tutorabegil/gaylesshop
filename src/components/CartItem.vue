<template>
    <div class="cart-item-container">
      <span>{{ item.name }} - Php {{ item.price }} x {{ item.quantity }}</span>
      <button @click="removeFromCart" class="remove-btn">Remove</button>
    </div>
  </template>
  
<script>
export default {
  // Define props that will be passed to this component
  props: ['item'],
  // Define methods that can be called within this component
  methods: {
    // Method to emit 'remove-from-cart' event with the item to be removed
    removeFromCart() {
      this.$emit('remove-from-cart', this.item);
    }
  }
};
</script>
  
  <style>
  .cart-item-container {
    display: flex;
    align-items: center;
  }
  
  .remove-btn {
    background-color: #007bff;
    color: #fff;
    border: none;
    padding: 5px 10px;
    font-size: 14px;
    cursor: pointer;
    margin-left: 10px;
  }
  </style>
  