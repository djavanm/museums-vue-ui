<template>
  <article class="current-exhibit">
    <img :src="exhibit.primaryimageurl" class="select-img"/>
    <div class="select-info">
    <h3>{{exhibit.title}}</h3>
    <h3>Venue: {{exhibit.venues[0].name}}</h3>
    <h3 v-if="exhibit.venues[0].city">Location: {{exhibit.venues[0].city}}, {{exhibit.venues[0].state}}</h3>
    <h3 v-if="exhibit.people">Curated By:</h3>
    <div v-bind:key="index" v-for="(curator, index) in exhibit.people" >
      <p> {{curator.name}} </p>
    </div>
    </div>
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
    display: flex;
    justify-content: center;
  }

  .current-exhibit h3 {
    font-size: 1rem;
  }
  
  .select-img {
    height: 400px;
    width: 600px;
    padding-right: 5%;
  }

  .select-info {
    width: 500px;
    display: flex;
    flex-direction: column;
    align-items: center;
      padding-top: 10%;
    padding-left: 5%;
    text-align: center;
  }
</style>