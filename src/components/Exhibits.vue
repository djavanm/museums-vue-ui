<template>
  <section class="exhibits-container">
    <div class="navigation-btn-container">
    <button class='nav-btn' @click="$emit('get-more-exhibits', prevUrl)" :disabled="prevUrl === ''">Previous</button>
    <button class='nav-btn' @click="$emit('get-more-exhibits', nextUrl)" :disabled="nextUrl === ''" >Next</button>
    </div>
    <section class="exhibits" >
    <div v-bind:key="exhibit.id" v-for="exhibit in exhibits" >
      <ExhibitMiniCard v-bind:exhibit="exhibit" v-on:select-exhibit="$emit('select-exhibit', exhibit.id)" />
    </div>  
    </section>
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
  .exhibits-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 70%;
    justify-content: space-between;
    align-items: center;
    margin: 0 auto;
  }
  
  .exhibits {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
  }
</style>