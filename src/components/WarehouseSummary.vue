<template>
    <div>
        <h2>Warehouse Summary</h2>
        <p>Total Products: {{ totalProducts }}</p>
        <p>Total Quantity: {{ totalQuantity }}</p>
    </div>
</template>

<script>
export default {
    props: ['products'],
    computed: {
        totalProducts() {
            return this.products.length;
        },
        totalQuantity() {
            return this.products.reduce((sum, product) => sum + product.quantity, 0);
        }
    }
};
</script>