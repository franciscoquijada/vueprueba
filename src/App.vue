<template>
  <div id="wrapper">
    <nav class="navbar is-dark">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item">
          <h1><strong>Logo</strong></h1>
        </router-link>
      </div>
      <div class="navbar-menu" id="navbar-menu">
        <div class="navbar-end">
          <div v-for="category in categories" v-bind:key="category.id">
            <router-link to="/" class="navbar-item">{{
              category.name
            }}</router-link>
          </div>
          <input
            class="input is-primary mt-2"
            type="text"
            value="Buscador de productos y categorias"
            placeholder="Primary input"
          />

          <div class="navbar-item">
            <div class="buttons">
              <!-- <router-link to="/log-in" class="button is-light">Log in</router-link> -->
              <button class="button">
                <i class="fas fa-shopping-bag"></i>
                <span>Bolsa</span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </nav>
    <section class="section">
      <router-view />
    </section>
  </div>
</template>
<script>
import SideBar from "./components/Sidebar.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    SideBar,
  },
  data() {
    return {
      categories: [],
    };
  },
  mounted() {
    this.getCategories();
  },
  methods: {
    getCategories() {
      axios
        .get("http://sva.talana.com:8000/api/product-category/")
        .then((response) => {
          this.categories = response.data;
          //console.log(response.data);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "../node_modules/bulma";
</style>
