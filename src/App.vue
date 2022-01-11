<template>
  <div id="app">
    <Header @searchNameFilm="callAPI" />
    <Main :detailsSearch="films" />
  </div>
</template>

<script>
import axios from 'axios';

import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main
  },
  data: function () {
    return {
      TextFindedNameFilm: '',
      films: []
    }
  },
  methods: {
    // findedNameFilm: function (text) {
    //   this.TextFindedNameFilm = text
    // },
    callAPI: function (text) {
      this.TextFindedNameFilm = text
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: '8a8760c91e1065b616382aecc64c7eb0',
          query: this.TextFindedNameFilm
        }
      })
      .then((response) => {
        this.films = response.data.results
        console.log(this.films);
      })
    }
  }
};
</script>

<style lang="scss">
@import './style/General.scss'

</style>
