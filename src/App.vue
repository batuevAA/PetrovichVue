<template>
    <main class="grid container">
        <div class="sub_category_page">
            <div class="column_right column_right_products_container">
                <div class="product__area">
                    <ProductList/>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
import ProductList from './components/ProductList.vue'

export default {
    name: 'App',
    components: {
        ProductList
    }
}
</script>

<style>
</style>
