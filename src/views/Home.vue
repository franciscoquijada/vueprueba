<template>
  <div class="home">
    <div class="modal" v-show="showModal" @close="setShowModal(false)">
      <div class="modal-background"></div>
      <div class="modal-content">
        <!-- Any other Bulma elements you want -->
      </div>
      <button class="modal-close is-large" aria-label="close"></button>
    </div>
    <div class="row">
      <div
        class="column is-3"
        v-for="product in products"
        v-bind:key="product.id"
      >
        <div class="box">
          <figure class="image mb-4" @click="setShowModal">
            <img :src="product.photo" />
          </figure>
          <h3 class="is-size-4">{{ product.name }}</h3>
          <p class="is-size-6 has-text-grey">${{ product.price }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      products: [],
      showModal: false
    };
  },
  components: {},
  mounted() {
    this.getProducts();
  },
  methods: {
    setShowModal (param) {	
      alert("prueba", param);
    	this.showModal = param
    },
    getProducts() {
      axios
        .get("http://sva.talana.com:8000/api/product/")
        .then((response) => {
          this.products = response.data;
          console.log(response.data);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
<style>
.image {
  margin-top: -1.25rem;
  margin-left: -1.25rem;
  margin-right: -1.25rem;
}

.image img {
  height: 33rem;
}
</style>