<template>
  <div v-if="images">
    <ul>
      <li v-for="(image, index) in images" v-bind:key="index">
        <img :src="image.urls.regular" :alt="image.description">
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['images']
}
</script>