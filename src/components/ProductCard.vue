<template>
    <div class="product-card">
        <img :src="product.image" alt="Product Image" class="product-image" />
        <h2 class="product-title">{{ product.title }}</h2>
        <p class="product-description">{{ product.description }}</p>
        <p class="product-price">{{ product.price | currency }}</p>
        <button @click="addToCart(product)" class="add-to-cart-button">Add to Cart</button>
    </div>
</template>

<script>
export default {
    name: 'ProductCard',
    props: {
        product: {
            type: Object,
            required: true
        }
    },
    methods: {
        addToCart(product) {
            this.$emit('add-to-cart', product);
        }
    }
}
</script>

<style scoped>
.product-card {
    border: 1px solid #ddd;
    padding: 16px;
    border-radius: 8px;
    text-align: center;
}
.product-image {
    max-width: 100%;
    height: auto;
}
.product-title {
    font-size: 1.5em;
    margin: 16px 0;
}
.product-description {
    font-size: 1em;
    color: #666;
}
.product-price {
    font-size: 1.2em;
    color: #333;
    margin: 16px 0;
}
.add-to-cart-button {
    background-color: #42b983;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 4px;
}
.add-to-cart-button:hover {
    background-color: #369f6e;
}
</style>