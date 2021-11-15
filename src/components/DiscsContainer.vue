<template>
  <div class="discs_container py-5">
    <div class="container d-flex justify-content-around">
      
      <div class="card mb-3 p-3 text-center" style="width: 15rem;" v-for="(disc, i) in discList" :key="i">
        <img :src="disc.poster" class="card-img-top" alt="">
        <div class="card-body">
          <h5 class="card-title fw-bold mb-4">{{ disc.title.toUpperCase() }}</h5>
          <p class="card-text mb-0">{{disc.author}}</p>
          <p class="card-text">{{disc.year}}</p>
        </div>
      </div>
      
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "DiscsContainer",
  data() {
    return {
      discList: "",
    }
  },
  mounted() {
    axios.get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((resp) => {
        this.discList = resp.data.response;
      })
  }
}
</script>

<style scoped lang="scss">

</style>