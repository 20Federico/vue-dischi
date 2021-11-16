<template>
  <div id="app">
    <Header></Header>
    <DiscsContainer></DiscsContainer>
  </div>
</template>

<script>
import 'bootstrap';
import DiscsContainer from './components/DiscsContainer.vue';
import Header from './components/Header.vue';

export default {
  name: 'App',
  components: {
    DiscsContainer,
    Header
  }
}
</script>

<style lang="scss">
  @import "@/styles/app"

</style>
