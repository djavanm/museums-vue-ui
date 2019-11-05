<template>
  <section class="exhibit-container"> 
    <h1>This is Exhibits</h1>
    <div v-bind:key="exhibit.id" v-for="exhibit in exhibits">
      <ExhibitMiniCard v-bind:exhibit="exhibit" />
    </div>
  </section>
</template>

<script>
import ExhibitMiniCard from './ExhibitMiniCard';
export default {
  name: "Exhibits",
  components: {
    ExhibitMiniCard
  },
  props: ["exhibits"]
}
</script>

<style scoped>
  .exhibit-container {
    border: 1px solid black;
    border-radius: 2px;
  }
</style>