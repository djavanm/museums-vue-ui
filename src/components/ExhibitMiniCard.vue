<template>
  <article class="exhibit-mini-card">
    <img :src="exhibit.primaryimageurl" alt="Exhibit picture" class="exhibit-picture"/>
    <button @click="$emit('select-exhibit', exhibit.id)" class="select-exhibit-btn"> More Info </button>
  </article>
</template>

<script>
export default {
  name: "ExhibitMiniCard",
  props: ["exhibit"]
}
</script>

<style scoped>
  .exhibit-mini-card {
    height: 120px;
    width: 120px;
    border: 2px solid red;
    border-radius: 2px;
  }
  .exhibit-picture {
    height: 100px;
    width: 100px;
  }

  .select-exhibit-btn {
    background: black;
    height: 25px;
    width: 30px;
    color: white;

  }
</style>