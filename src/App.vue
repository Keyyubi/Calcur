<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col">
        <h1>Calculate your Waybook ROI</h1>
      </div>
    </div>
    <div class="row mb-5">
      <div class="col">
        Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
      </div>
    </div>
    <div class="row mt-5">
      <Card />
    </div>
  </div>
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'App',
  components: {
    Card
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Sen:wght@400;700;800&display=swap');

#app {
  font-family: 'Sen', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  font-weight: 700 !important;
}
</style>
