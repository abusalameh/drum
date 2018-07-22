<template>
  <div id="app">
    <Drum/>
  </div>
</template>

<script>
import Drum from './components/Drum'

export default {
  name: 'App',
  components: {
    Drum
  }
}
</script>

<style>
html {
  font-size: 10px;
  background:url(/static/abstract-music-rock-bw.jpg) bottom center;
  background-size: cover;
}
body,html {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
}

</style>
