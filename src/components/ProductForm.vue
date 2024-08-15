<template>
  <div>
    <h2>Add New Product</h2>
    <form @submit.prevent="addProduct">
      <div>
        <label>Product Name:</label>
        <input v-model="name" required />
      </div>
      <div>
        <label>SKU:</label>
        <input v-model="sku" required />
      </div>
      <div>
        <label>Quantity:</label>
        <input type="number" v-model.number="quantity" required min="1" />
      </div>
      <button type="submit">Add Product</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      sku: '',
      quantity: 0
    };
  },
  methods: {
    addProduct() {
      const newProduct = {
        name: this.name,
        sku: this.sku,
        quantity: this.quantity
      };
      this.$emit('add-product', newProduct);
      this.name = '';
      this.sku = '';
      this.quantity = 0;
    }
  }
};
</script>
