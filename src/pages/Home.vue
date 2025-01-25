<template>
    <div>
      <Searchbar @search="handleSearch" />
        <div class="flex space-x-4 my-4">
            <select v-model="selectedCategory" class="border px-2 py-1 rounded">
                <option value="">All Categories</option>
                <option v-for="category in categories" :key="category" :value="category">
                {{ category }}
                </option>
            </select>
            <input
                type="number"
                v-model="minPrice"
                placeholder="Min Price"
                class="border px-2 py-1 rounded"
            />
            <input
                type="number"
                v-model="maxPrice"
                placeholder="Max Price"
                class="border px-2 py-1 rounded"
            />
        </div>
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <ProductCard
          v-for="product in filteredProducts"
          :key="product.id"
          :product="product"
        />
      </div>
    </div>
  </template>
  
  <script>
  import Searchbar from '../components/Searchbar.vue';
  import ProductCard from '../components/ProductCard.vue';
  import { fetchProducts } from '../api/products';
  
  export default {
    components: { Searchbar, ProductCard },
    data() {
      return {
        products: [],
        searchQuery: '',
        selectedCategory: '',
        minPrice: null,
        maxPrice: null,
        categories: ['electronics', 'jewelery', 'men\'s clothing', 'women\'s clothing'],
      };
    },
    computed: {
    filteredProducts() {
        return this.products
        .filter((product) =>
            product.title.toLowerCase().includes(this.searchQuery.toLowerCase())
        )
        .filter((product) =>
            this.selectedCategory ? product.category === this.selectedCategory : true
        )
        .filter((product) =>
            this.minPrice ? product.price >= this.minPrice : true
        )
        .filter((product) =>
            this.maxPrice ? product.price <= this.maxPrice : true
        );
    },
    },
    async created() {
      this.products = await fetchProducts();
    },
    methods: {
      handleSearch(query) {
        this.searchQuery = query;
      },
    },
  };
  </script>
  