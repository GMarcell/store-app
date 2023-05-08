<template>
  <div>
    <NavigationBar/>
    <div class="product-page">
      <div class="left">
        <img :src="`${product.image}`" alt="poster" class="product-image"/>
      </div>
      <div class="right">
        <h1>{{ product.title }}</h1>
        <br/>
        <h2>{{ product.description }}</h2>
        <br/>
        <br/>
        <h2>Category : {{ product.category }}</h2>
        <h2>Price : {{ product.price }}</h2>
        <br/>
        <button>
          Add To Cart
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
import NavigationBar from '~/components/NavigationBar.vue'
export default {
    data() {
        return {
            product: ""
        };
    },
    async fetch() {
        await this.getSingleProduct();
    },
    head() {
        return {
            title: this.product.title
        };
    },
    methods: {
        async getSingleProduct() {
            const data = axios.get(`https://fakestoreapi.com/products/${this.$route.params.productId}`);
            const result = await data;
            this.product = result.data;
        }
    },
    components: { NavigationBar }
}
</script>
<style lang="scss" scoped>
.product-page{
  display: flex;
  padding: 30px;
  .left{
    .product-image{
      width:100%;
    }
  }
  .right{
    padding-left: 50px;
  }
}
</style>