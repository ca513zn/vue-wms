<template>
    <div>
        <h2>Update Product Quantity</h2>
        <form @submit.prevent="updateProduct">
            <div>
                <label>Select Product:</label>
                <select v-model="selectedProductIndex">
                    <option v-for="(product, index) in products" :key="index" :value="index">
                        {{ product.name }} ({{ product.sku }})
                    </option>
                </select>
            </div>
            <div>
                <label>New Quantity:</label>
                <input type="number" v-model.number="newQuantity" required min="1" />
            </div>
            <button type="submit">Update Quantity</button>
        </form>
    </div>
</template>

<script>
export default {
    props: ['products'],
    data() {
        return {
            selectedProductIndex: null,
            newQuantity: 0
        };
    },
    methods: {
        updateProduct() {
            if (this.selectedProductIndex !== null) {
                // Create a copy of the selected product
                const updatedProduct = { ...this.products[this.selectedProductIndex], quantity: this.newQuantity };

                // Emit an event to update the product in the parent component
                this.$emit('update-product', this.selectedProductIndex, updatedProduct);
            }
            this.newQuantity = 0;
            this.selectedProductIndex = null;
        }
    }
};
</script>