<template>
  <section class="exhibit-container"> 
    <h1>This is Exhibits</h1>
    <button @click="$emit('get-more-exhibits', prevUrl)" :disabled="prevUrl === ''">Previous</button>
    <div v-bind:key="exhibit.id" v-for="exhibit in exhibits">
      <ExhibitMiniCard v-bind:exhibit="exhibit" v-on:select-exhibit="$emit('select-exhibit', exhibit.id)"/>
    </div>
    <button @click="$emit('get-more-exhibits', nextUrl)" :disabled="nextUrl === ''" >Next</button>
  </section>
</template>

<script>
import ExhibitMiniCard from './ExhibitMiniCard';
export default {
  name: "Exhibits",
  components: {
    ExhibitMiniCard
  },
  props: ["exhibits", "nextUrl", "prevUrl"]
}
</script>

<style scoped>
  .exhibit-container {
    border: 1px solid black;
    border-radius: 2px;
  }
</style>