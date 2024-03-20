<template>
  <div>
    <h1 class="product-title" style="display: flex; font-size: 70px; margin-top: 20%; justify-content: center; align-items: center;;">GAYLE'S SNACK</h1>
    <div class="search-container">
      <h3 class="search-title">LIST OF GAYLE'S SNACK</h3>
      <input type="text" v-model="searchQuery" placeholder="Type here...">
    </div>
    <div class="product-container">
      <ul class="product-list">
        <li v-if="filteredProducts.length === 0" class="no-results">No matching snack found.</li>
        <li v-for="product in filteredProducts" :key="product.id" class="product-item">
          <div class="product-info">
            <img :src="product.image" alt="Product Image" class="product-image">
            <div>
              <p class="product-name">{{ product.name }}</p>
              <p class="product-price">Php {{ product.price }}</p>
            </div>
          </div>
          <button @click="addToCart(product)" class="add-to-cart-btn">Add snack to Cart</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  // Data function to initialize data properties
  data() {
    return {
      searchQuery: '', // Holds the search query entered by the user
      products: [ // Array of products with their details
        { id: 1, name: 'Alibaba', price: 25, image: '/img/alibaba.jpg' },
        { id: 2, name: 'Boy Bawang', price: 27, image: '/img/boybawang.jpg' },
        { id: 3, name: 'Cheez-It', price: 29, image: '/img/cheezit.jpg' },
        { id: 4, name: 'Clover', price: 26, image: '/img/clover.jpg' },
        { id: 5, name: 'Kobi', price: 20, image: '/img/kobi.jpg' },
        { id: 6, name: 'Lumpia', price: 22, image: '/img/lumpia.jpg' },
        { id: 7, name: 'Nagaraya', price: 20, image: '/img/nagaraya.jpg' },
        { id: 8, name: 'Piattos', price: 15, image: '/img/piatos.jpg' },
        { id: 9, name: 'V-Cut', price: 170, image: '/img/vcut.jpg' }
      ]
    };
  },
  // Computed property to filter products based on search query
  computed: {
    filteredProducts() {
      if (!this.searchQuery.trim()) {
        return this.products; // Return all products if search query is empty
      }
      const query = this.searchQuery.toLowerCase();
      return this.products.filter(product =>
        product.name.toLowerCase().includes(query)
      );
    }
  },
  // Method to emit 'add-to-cart' event with selected product
  methods: {
    addToCart(product) {
      this.$emit('add-to-cart', product);
    }
  }
};
</script>


<style>

.product-title {
 
  color: orangered;
  margin-bottom: 20px;
}

.search-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.search-title {
  font-size: 20px;
  color: #000; /* black color */
  margin-bottom: 50px;
  
}


input[type="text"] {
  width: 500px;
  padding: 10px;
  font-size: 16px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

.input-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.product-container {
  background-color:  skyblue;
  opacity: 80%;
  margin-top: 30px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 100px;
}

.product-list {
  list-style: none;
  padding: 0;
  display: grid;
  grid-template-columns: repeat(3, 1fr); 
  gap: 20px; 
}

.product-item {
  background-color: transparent;
  opacity: 120%;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0px 0px 10px rgba(255, 0, 0, 0.708);
  display: flex;
  flex-direction: column;
  
}

.product-info {
  display: flex;
  align-items: center;
}

.product-image {
  width: 80px;
  height: 80px;
  border-radius: 10px;
  border: 2px solid transparent;
  margin-right: 20px;
}

.product-name {
  color: #000;
}

.product-price {
  color: #000;
}

.add-to-cart-btn {
  background-color: #0f0; /* green color */
  color: #000;
  border: none;
  padding: 8px 15px;
  font-size: 12px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.add-to-cart-btn:hover {
  background-color: #ffc107;
  color: #000;
}

.no-results {
  color: #ff0;
  font-style: italic;
}
</style>
