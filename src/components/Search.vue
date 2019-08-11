<template>
  <div class="search">
    <h1>Unsplash</h1>
    <p>The internet’s source of freely useable images.</p>
    <label>
      <input type="text" v-model="query" @keypress.enter="handleSearch" placeholder="Search free high-resolution photos" />
    </label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: ''
    }
  }, 
  methods: {
    handleSearch() {
      this.$emit('searchRequested', this.query);
    }
  }
}
</script>
