<template>
  <div class="discs_container py-5">
    <div class="container d-flex justify-content-around">
      <Loader v-if="loading"></Loader>
      <Filters @toFilter="genreToFilter" :genres="genreList"></Filters>
      <Card :disc="disc" v-for="(disc, i) in filteredDiscList" :key="i"></Card>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from './Card.vue';
import Loader from './Loader.vue';
import Filters from './Filters.vue';

export default {
  name: "DiscsContainer",
  components: { 
    Card, 
    Loader, 
    Filters 
  },
  data() {
    return {
      loading: true,
      discList: "",
      filteredDiscList: [],
      genreList: []
    }
  },
  methods: {
    genreToFilter(toSearchGenre) {
      console.log('function');
      if (toSearchGenre === 'Tutti') {
        this.filteredDiscList = this.discList   
      } else {
        this.filteredDiscList = this.discList.filter(element => element['genre'] === toSearchGenre )
      }
    }
  },
  mounted() {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.discList = resp.data.response;
        this.filteredDiscList = this.discList
        setTimeout(() => {
        return this.loading = false;
        }, 500)
        this.discList.forEach(element => {
          if (this.genreList.includes(element['genre'])) {
            return;          
          } else {
            this.genreList.push(element['genre']);
          }
        });
      }) 
  }
}
</script>