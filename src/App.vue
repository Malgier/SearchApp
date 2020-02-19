<template>
  <div id="app" class="row">
    <div class="col-md-3"></div>
    <div class="col-md-6">
      <Results />
    </div>
    <div class="col-md-3"></div>
  </div>
</template>

<script>
import Results from "./components/Results.vue";
import Vue from "vue";
import { BootstrapVue } from "bootstrap-vue";
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";

// Install BootstrapVue
Vue.use(BootstrapVue);

export default {
  name: "App",
  components: {
    Results
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
