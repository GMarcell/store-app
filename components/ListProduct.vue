<template>
    <div>
      <div class="products-container" id="product-grid">
        <div v-for="(product, index) in products" :key="index" class="test">
          <div class="product">
            <img :src="`${product.image}`" alt="poster" class="product-image"/>
            <div class="info">
              <h2>
                {{ product.title.slice(0, 25) }}
                <span v-if="product.title.length > 25">...</span>
              </h2>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  <script>
  import axios from 'axios'
  export default {
    data(){
      return {
        products: []
      }
    },
    async fetch(){
      await this.getProducts()
    },
    methods: {
      async getProducts(){
        const data = axios.get(
          'https://fakestoreapi.com/products'
        )
        const result = await data
        result.data.forEach(element => {
          this.products.push(element)
        })
      }
    }
  }
  </script>
  <style lang="scss" scoped>
    .products-container{
      padding: 32px 16px;
      display: grid;
      column-gap: 32px;
      row-gap: 64px;
      grid-template-columns: 1fr;
      @media (min-width: 500px) {
        grid-template-columns: repeat(2, 1fr);
      }
      @media (min-width: 750px) {
        grid-template-columns: repeat(3, 1fr);
      }
      @media (min-width: 1100px) {
        grid-template-columns: repeat(4, 1fr);
      }
    }
    .test{
      background-color: white;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .product{
      position: relative;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      .product-image{
        width: 100%;
        img {
          display: block;
          width: 100%;
          height: 100%;
        }
      }
      .info{
          text-align: center;
          bottom: 0;
        }
    }
  </style>