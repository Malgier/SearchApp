<template>
  <div class="results">
    <Search
      :pageLimit="pageLimit"
      :pageNumber="pageNumber"
      @productsLoaded="handleProducts"
    />
    <div class="row centre-grid">
      <div v-for="product in products" :key="product">
        <div class="box shadow">
          <img v-bind:src="product.image_url" class="image max-size" />
          <p>{{ product.title }}</p>
          <p>
            From {{ displayCurrency(product.price.currency)
            }}{{ product.price.max }}
          </p>
          <form v-bind:action="product.link">
            <button type="submit" class="button">View</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Search from "./Search.vue";

export default {
  name: "results",
  components: {
    Search
  },
  props: {
    msg: String
  },

  data() {
    return {
      products: null,
      pageLimit: 10,
      pageNumber: 1,
      currency: ""
    };
  },

  mounted() {},

  methods: {
    handleProducts(value) {
      this.products = value;
    },

    displayCurrency(currency) {
      switch (currency) {
        case "GBP":
          return "£";
        case "EURO":
          return "€";
        case "USD": {
          return "$";
        }
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.box {
  text-align: center;
  border-radius: 5px;
  margin: 20px;
  max-width: 275px;
  float: none;
  min-height: 380px;
}

.shadow {
  box-shadow: 0px 0px 4px 1px rgba(0, 0, 0, 0.2);
}

.max-size {
  max-width: 200px;
}

.button {
  width: 80%;
  color: white;
  background: black;
  border: none;
  margin: 5px;
  border-radius: 5px;
}

.centre-grid {
  display: inline-grid;
  grid-template-columns: auto auto;
}
</style>
