<template>
  <div class="page-product">
    <div class="columns is-multiline">
      <figure class="image mb-6">
        <img :src="product.photo" />
      </figure>
      <h1 class="title">
        {{ product.name }}
      </h1>
      <p>{{ product.description }}</p>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "Product",
  data() {
    return {};
  },
};
</script>