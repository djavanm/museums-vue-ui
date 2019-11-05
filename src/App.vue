<template>
  <div id="app">
    <p>hi, I'm an App</p>
    <Exhibits v-bind:exhibits="exhibits" />
  </div>
</template>

<script>
import Exhibits from './components/Exhibits';
export default {
  name: 'app',
  components: {
    Exhibits
  },
  data() {
    return {
      exhibits: [],
      next: '',
      prev: '',
      current: {}
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
