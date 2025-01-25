<template>
    <div class="cart">
        <h1>Shopping Cart</h1>
        <div v-if="cartItems.length === 0">
            <p>Your cart is empty.</p>
        </div>
        <div v-else>
            <ul>
                <li v-for="item in cartItems" :key="item.id">
                    <span>{{ item.name }}</span>
                    <span>{{ formatCurrency(item.price) }}</span>
                    <button @click="removeFromCart(item.id)">Remove</button>
                </li>
            </ul>
            <div class="total">
                <span>Total: {{ formatCurrency(total) }}</span>
            </div>
            <button @click="checkout">Checkout</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            cartItems: [
                { id: 1, name: 'Product 1', price: 10.0 },
                { id: 2, name: 'Product 2', price: 20.0 },
            ],
        };
    },
    computed: {
        total() {
            return this.cartItems.reduce((sum, item) => sum + item.price, 0);
        },
    },
  
    methods: {
        removeFromCart(id) {
            this.cartItems = this.cartItems.filter(item => item.id !== id);
        },
        checkout() {
            alert('Proceeding to checkout');
        },
        formatCurrency(value) {
            return `$${value.toFixed(2)}`;
        },
    },
};
</script>

<style scoped>
.cart {
    padding: 20px;
}
.cart ul {
    list-style-type: none;
    padding: 0;
}
.cart li {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
}
.total {
    margin-top: 20px;
    font-weight: bold;
}
</style>