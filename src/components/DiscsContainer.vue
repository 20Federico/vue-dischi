<template>
  <div class="discs_container py-5">
    <div class="container d-flex justify-content-around">
      <Loader v-if="loading"></Loader>
      <Filters @toFilter="genreToFilter" :genres="genreList"></Filters>
      <Card :disc="disc" v-for="(disc, i) in toFilterGenre" :key="i"></Card>
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
      genreList: [],
      selectedGenre: ""
    }
  },
  methods: {
    genreToFilter(toSearchGenre) {
      this.selectedGenre = toSearchGenre
    }
  },
  computed: {
    toFilterGenre() {
      if (this.selectedGenre === 'Tutti' || !this.selectedGenre) {
        return this.discList   
      } else {
        return this.discList.filter(element => element['genre'] === this.selectedGenre )
      }
    }
  },
  mounted() {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.discList = resp.data.response;
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