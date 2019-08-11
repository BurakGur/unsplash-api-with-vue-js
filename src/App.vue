<template>
  <div id="app">
    <search v-on:searchRequested="handleSearch"></search>
    <div class="loading" v-if="isLoading"><img src='./assets/loading.gif'></div>
    <preview v-bind:images=images></preview>
  </div>
</template>

<script>
import Search from './components/Search'
import Preview from './components/Preview'

export default {
  name: 'app',
  components: { Search, Preview },
  data() {
    return {
      isLoading: true,
      images: []
    }
  },
  methods: {
    handleSearch(query) {
      this.images = []
      this.isLoading = true; 
      fetch(`https://api.unsplash.com/search/photos?page=1&query=${query}&client_id=YOUR_CLIENT_ID`)
        .then((res) => { return res.json() } )
        .then((res) => { 
          this.images = res.results; 
          this.isLoading = false;
      })
    }
  },
  created() {
    this.isLoading = false;
  }
}
</script>

<style lang="sass">
  @import './assets/main.sass';
</style>
