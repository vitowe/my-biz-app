<template>
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
    <ProductCard v-for="product in products" :key="product.id" :product="product" />
</div>
</template>

<script>
import { fetchProducts } from '../api/products';
import ProductCard from '../components/ProductCard.vue';

export default {
components: { ProductCard },
data() {
    return { products: [] };
},
async created() {
    this.products = await fetchProducts();
},
};
</script>
    