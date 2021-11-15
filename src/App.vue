<template>
  <div id="app">
    <nav>
      <img class="py-3 ps-3" src="@/assets/logo-small.svg" alt="spotify logo">
    </nav>
    <DiscsContainer></DiscsContainer>
  </div>
</template>

<script>
import 'bootstrap';
import DiscsContainer from './components/DiscsContainer.vue';

export default {
  name: 'App',
  components: {
    DiscsContainer
    
  }
}
</script>

<style lang="scss">
@import "@/styles/app"

</style>
