<template>
  <div class="filters_container container pb-5">
    <label for="genere" class="text-white pe-4">Filtra per genere:</label>
    <select v-model="selected" class="py-1 px-2 me-3" name="genere">
      <option value="Tutti">Tutti</option>
      <option v-for="(genre, i) in genres" :key="i" :value="genre">{{genre}}</option>
    </select>
    <button class="py-1 px-2" type="button" @click="$emit('toFilter', selected)">FILTRA!</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: 'Tutti'
    }
  },
  props: ["genres"]
}
</script>
