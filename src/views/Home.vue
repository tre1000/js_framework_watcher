<template>
  <div class="home">
    <h1>Vue.js</h1>
    <h3>{{ vueWatchers }}</h3>
    <br>
    <h1>Angular</h1>
    <h3>{{ angularWatchers }}</h3>
    <br>
    <h1>Svelte</h1>
    <h3>{{ svelteWatchers }}</h3>
    <br>
    <h1>React</h1>
    <h3>{{ reactWatchers }}</h3>
    <br>
  </div>
</template>

// bootstrap, jquery, and jspopper are already installed. Look into bootstrap graphs and shit.

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      vueWatchers: "",
      angularWatchers: "",
      svelteWatchers: "",
      reactWatchers: "",
    }
  },

  created: function () {
    this.getWatchers();
  },

  methods: {
    getWatchers: function () {
      //Vue.js
      axios.get("https://api.github.com/repos/vuejs/vue").then((response) => {
        this.vueWatchers = response.data.watchers_count;
      });
      //angular
      axios.get("https://api.github.com/repos/angular/angular.js").then((response) => {
        this.angularWatchers = response.data.watchers_count;
      });
      //svelte
      axios.get("https://api.github.com/repos/sveltejs/svelte").then((response) => {
        this.svelteWatchers = response.data.watchers_count;
      });
      //react
      axios.get("https://api.github.com/repos/facebook/react").then((response) => {
        this.reactWatchers = response.data.watchers_count;
      });
    },
  }
}
</script>
