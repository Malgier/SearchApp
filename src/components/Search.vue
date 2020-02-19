<template>
  <div class="row content">
    <input
      class="text search"
      v-model="query"
      placeholder="search..."
      v-on:keyup="search"
    />
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "search",
  props: {
    pageLimit: Number,
    pageNumber: Number
  },

  data() {
    return {
      url: "https://aix.salesfire.co.uk/api/searcha",
      clientId: "3f32397c-21c6-47e5-9ebd-e9865ea03470",
      query: "",
      timeout: null
    };
  },

  mounted() {
    this.search();
  },

  methods: {
    constructURL: function() {
      return (
        this.url +
        "?client_id=" +
        this.clientId +
        "&query=" +
        this.query +
        "&limit=" +
        this.pageLimit +
        "&page=" +
        this.pageNumber
      );
    },

    search: function() {
      const self = this;
      clearTimeout(self.timeout);
      self.timeout = setTimeout(function() {
        var url = self.constructURL();
        axios.get(url).then(res => self.handleResponse(res));
      }, 1000);
    },

    handleResponse: function(response) {
      this.$emit("productsLoaded", response.data.products);
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

.content {
  width: 80%;
  margin: 0 10%;
}

.search {
    width: 100%;
    font-weight: bold;
}
</style>
