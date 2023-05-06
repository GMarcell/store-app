<template>
  <div class="home">
    <NavigationBar/>
    <HeroBanner/>
    <ListProduct/>
  </div>
</template>

<script>
import ListProduct from '~/components/ListProduct.vue';
import NavigationBar from '~/components/NavigationBar.vue';

export default {
    name: "IndexPage",
    components: { ListProduct, NavigationBar }
}
</script>
