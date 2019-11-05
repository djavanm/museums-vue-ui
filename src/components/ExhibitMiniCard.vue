<template>
  <article class="exhibit-mini-card">
    <img 
    :src="exhibit.primaryimageurl" alt="Exhibit picture" class="exhibit-picture"
    @click="$emit('select-exhibit', exhibit.id)"
    />
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
    height: 200px;
    width: 200px;
    margin: 5px 5px;
  }
  
  .exhibit-mini-card:hover {
    box-shadow: 0px 6px 15px 0px rgba(0,0,0,0.75);
  }

  .exhibit-picture {
    height: 100%;
    width: 100%;
    cursor: pointer;
  }

  .select-exhibit-btn {
    background: black;
    height: 25px;
    width: 30px;
    color: white;
  }
</style>