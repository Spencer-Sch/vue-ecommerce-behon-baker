<template>
  <div>
    <Nav />
    <HomeCarousel :sale_items="sale_items" />
    <br />
    <v-container>
      <h1 class="text-md-h4 text-h6">Check these out</h1>
      <br />
      <ProductSlider :products="products" />
    </v-container>
    <br /><br /><br />
    <Newsletter />
    <Footer />
  </div>
</template>

<script>
import HomeCarousel from "~/components/HomeCarousel.vue";
import ProductSlider from "~/components/ProductSlider.vue";
import Newsletter from "~/components/Newsletter.vue";
export default {
  async created() {
    this.sale_items = await this.$content("products")
      .where({ onSale: true })
      .fetch();
    this.products = await this.$content("products").fetch();
  },
  data() {
    return {
      products: null,
      sale_items: null,
    };
  },
  components: { HomeCarousel, ProductSlider, Newsletter },
};
</script>
<style></style>
