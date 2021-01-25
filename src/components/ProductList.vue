<template>
    <div id="products_section">   
        <div class="products_page pg_0" v-for="product in products" :key="product.productId">
            <Product :product = "product"/>
        </div>
    </div>
</template>

<script>
import products from '../../products.json';
import Product from './Product.vue';

export default {
    name: 'ProductList',
    components: { 
        Product 
    },
    data() {
        return {
            products
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
