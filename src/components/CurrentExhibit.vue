<template>
  <article class="current-exhibit">
    <h2>Current Exhibit </h2>
    <img :src="exhibit.primaryimageurl" />
  </article>
</template>

<script>
export default {
  name: "CurrentExhibit",
  props: ["exhibit"]
}
</script>

<style scoped>
  .current-exhibit {
    border: 2px solid yellow;
  }
</style>