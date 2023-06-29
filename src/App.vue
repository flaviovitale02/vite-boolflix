<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";
import { store } from "./store"


export default {
  data() {
    return {
      store,
    };

  },

  components: {
    AppHeader,
    AppMain,
  },



  methods: {
    RequestDataFromApi() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: "3230330c1c509c72a0be97deca021c40",
            query: this.store.SearchBar,
          },
        })
        .then((response) => (this.store.ArrMovies = response.data.results));

      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: "3230330c1c509c72a0be97deca021c40",
            query: this.store.SearchBar,
          },
        })
        .then((response) => (this.store.ArrTvSeries = response.data.results));
    },

    created() {
      this.RequestDataFromApi()
    },
  },
};
</script>

<template>
  <AppHeader @searchPerformed="RequestDataFromApi" />
  <AppMain />
</template>





<!-- INIZIO STILE  -->
<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>

