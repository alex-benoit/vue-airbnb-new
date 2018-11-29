<template>
  <div class="container">
    <div class="main">
      <div class="flats">
        <flat v-for="flat in flats" v-bind="flat" v-on:selectedFlatChanged="changeSelectedFlat"></flat>
      </div>
    </div>
    <panel v-bind="this.selectedFlat"></panel>
  </div>
</template>

<script>
import flat from './Flat.vue';
import panel from './Panel.vue';

export default {
  data () {
    return {
      flats: [],
      selectedFlat: null
    }
  },
  methods: {
    changeSelectedFlat(id) {
      console.log(id)
      this.selectedFlat = this.flats.find(flat => flat.id == id)
    }
  },
  components: { flat, panel },
  mounted: function() {
   this.$http.get('https://raw.githubusercontent.com/alex-benoit/flats-json/master/flats.json')
    .then(response => response.json())
    .then(data => {
      this.flats = data
      this.selectedFlat = this.flats[0]
    })
  }
}
</script>

<style>
.container {
  display: grid;
  grid-template-columns: 2fr 1fr;
}
.main {
  grid-column: 1 / span 1;
}
.panel {
  grid-column: 2 / span 1;
}
.flats {
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
}
</style>
