<template>
    <div class="container mx-auto px-4 py-3 flex justify-between items-center">
    <input
        v-model="searchQuery"
        @input="onSearch"
        class="border px-2 py-1 rounded"
        placeholder="Search products..."
    />
    </div>
  </template>
  
  <script>
  export default {
    name: 'Searchbar',
    data() {
      return {
        searchQuery: '',
      };
    },
    methods: {
      onSearch() {
        this.$emit('search', this.searchQuery);
      },
    },
  };
  </script>
  