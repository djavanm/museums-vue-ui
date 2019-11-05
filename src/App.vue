<template>
  <div id="app">
    <nav>
      <h1>Art Info</h1>
    </nav>
    <CurrentExhibit v-if="current" v-bind:exhibit="current" />
    <Exhibits 
      v-if="exhibits.length"
      v-bind:exhibits="exhibits" 
      v-bind:nextUrl="next"
      v-bind:prevUrl="prev"
      v-on:select-exhibit="selectExhibit" 
      v-on:get-more-exhibits="getMoreExhibits"
    />
  </div>
</template>

<script>
import Exhibits from './components/Exhibits';
import CurrentExhibit from './components/CurrentExhibit';

export default {
  name: 'app',
  components: {
    Exhibits,
    CurrentExhibit
  },
  data() {
    return {
      exhibits: [],
      next: '',
      prev: '',
      current: null
    }
  },
  created() {
    const url = `https://api.harvardartmuseums.org/exhibition?venue=HAM&hasimage=1&apikey=${process.env.VUE_APP_API_KEY}`
    fetch(url)
      .then(res => res.json())
      .then(data => {
        this.exhibits = data.records;
        this.next = data.info.next;
        this.current = data.records[0];
      });
  },
  methods: {
    selectExhibit(id) {
      const url = `https://api.harvardartmuseums.org/exhibition/${id}?apikey=${process.env.VUE_APP_API_KEY}`
      fetch(url)
        .then(res => res.json())
        .then(data => this.current = data)
    },
    getMoreExhibits(url) {
      fetch(url)
        .then(res => res.json())
        .then(data => {
          this.exhibits = data.records;
          this.next = data.info.next ? data.info.next : '';
          this.prev = data.info.prev ? data.info.prev : '';
        });
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

</style>
