<template>
    <div class="product-page">
        <h1>Product Page</h1>
        <div class="product-details">
            <h2>Product Name</h2>
            <p>Description of the product goes here.</p>
            <p>Price: $0.00</p>
            <button>Add to Cart</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProductPage',
    data() {
        return {
            product: {
                name: 'Sample Product',
                description: 'This is a sample product description.',
                price: 0.00
            }
        };
    },
    methods: {
        addToCart() {
            console.log('Product added to cart');
        }
    }
};
</script>

<style scoped>
.product-page {
    padding: 20px;
}

.product-details {
    border: 1px solid #ccc;
    padding: 10px;
    margin-top: 20px;
}

button {
    background-color: #007BFF;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}
</style>
