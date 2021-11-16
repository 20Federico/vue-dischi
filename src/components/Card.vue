<template>
  <div class="card mb-3 p-3 text-center" style="width: 15rem;">
    <img :src="disc.poster" class="card-img-top" alt="">
    <div class="card-body">
      <h5 class="card-title fw-bold mb-4">{{ disc.title.toUpperCase() }}</h5>
      <p class="card-text mb-0">{{disc.author}}</p>
      <p class="card-text">{{disc.year}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["disc"]
}
</script>