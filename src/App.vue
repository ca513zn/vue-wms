<template>
  <div id="app">
    <ProductForm @add-product="addProduct" />
    <UpdateProduct :products="products" @update-product="handleProductUpdate" />
    <WarehouseSummary :products="products" />
  </div>
</template>

<script>
import ProductForm from './components/ProductForm.vue';
import UpdateProduct from './components/UpdateProduct.vue';
import WarehouseSummary from './components/WarehouseSummary.vue';

export default {
  components: {
    ProductForm,
    UpdateProduct,
    WarehouseSummary
  },
  data() {
    return {
      products: []
    };
  },
  methods: {
    addProduct(newProduct) {
      this.products.push(newProduct);
    },
    handleProductUpdate(index, updatedProduct) {
      this.products.splice(index, 1, updatedProduct);
    }
  }
};
</script>
