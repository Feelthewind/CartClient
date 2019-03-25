<template>
  <table class="table is-hoverable is-fullwidth">
    <tbody>
      <CartOverviewProduct
        v-for="product in products"
        :key="product.id"
        :product="product"
      />
    </tbody>
  </table>
</template>

<script>
import { mapGetters } from "vuex";

import CartOverviewProduct from "@/components/cart/CartOverviewProduct";

export default {
  computed: {
    ...mapGetters({
      products: "cart/products"
    })
  },

  components: {
    CartOverviewProduct
  }
};
</script>

<style>
</style>
