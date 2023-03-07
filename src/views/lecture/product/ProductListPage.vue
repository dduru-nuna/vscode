<template>
  <div>
    <section class="wrapper">
        <h2>Items</h2>
        <ul class="items">
            <li v-for="product in products" :key="product.id" class="items_item">
                <img class="product-image" :src="imagePath(product)" alt="">
                <p class="product-title">{{ product.name }}</p>
                <p><em>{{ product.price }}won</em></p>
            </li>
        </ul>
    </section>
  </div>
</template>

<script>
export default {
    name: 'ProductListPage',
    computed: {
       products: function() {
        return this.$store.state.products
       }
    },
    methods: {
        imagePath(product) {
            return require(`D:/proj/GitHub/vscode/src/assets/img/products/${product.images[0]}`);
        }
    }
}
</script>

<style>

</style>