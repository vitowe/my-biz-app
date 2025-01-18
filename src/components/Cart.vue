<template>
    <div class="cart">
        <h1>Your Cart</h1>
        <ul>
            <li v-for="item in cartItems" :key="item.id">
                {{ item.name }} - {{ item.price | currency }}
                <button @click="removeFromCart(item.id)">Remove</button>
            </li>
        </ul>
        <p v-if="cartItems.length === 0">Your cart is empty.</p>
        <p>Total: {{ total | currency }}</p>
        <button @click="checkout" :disabled="cartItems.length === 0">Checkout</button>
    </div>
</template>

<script>
export default {
    name: 'Cart',
    data() {
        return {
            cartItems: [
                { id: 1, name: 'Item 1', price: 10 },
                { id: 2, name: 'Item 2', price: 20 },
            ],
        };
    },
    computed: {
        total() {
            return this.cartItems.reduce((sum, item) => sum + item.price, 0);
        },
    },
    methods: {
        removeFromCart(itemId) {
            this.cartItems = this.cartItems.filter(item => item.id !== itemId);
        },
        checkout() {
            alert('Proceeding to checkout');
        },
    },
    filters: {
        currency(value) {
            return `$${value.toFixed(2)}`;
        },
    },
};
</script>

<style scoped>
.cart {
    padding: 20px;
    border: 1px solid #ccc;
}
</style>