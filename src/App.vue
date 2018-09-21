<template>
  <div id="app">
    <Main/>
    <div class="introduction">
      <div class="introduction-content">
        Choosing where you want to live when you retire is often seen as a big decision — but it’s also an exciting one. After all, this next phase is one where you’ll have more time to devote to your favorite pursuits, whether that’s traveling, volunteering, spending more time with loved ones or being even more active in your community.
The big question, though, is how do you find a place that meets your core interests? Your ideal lifestyle for retirement might be anchored in the great outdoors; include access to the best of art, food and culture; or be designed to keep your cost of living modest. Since those three qualities loom large for many people, we conducted a unique study to identify and rank the top 10 cities for those three distinct priorities, represented in the maps below.
The final destination that you’ll call home? We’ll leave that to you.
      </div>
        <div class="map-wrapper">
      </div>
    </div>
  </div>
</template>

<script>
import Main from './components/Main'

export default {
  name: 'App',
  components: {
    Main
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  .introduction {
  border: solid 1px black;

  height: 500px;
  .introduction-content {
    position: absolute;
    top: 35%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 80%;
    line-height: 100px;
    }
  }
  .map-wrapper {
    width: 100%;
    height: 500px;
    background-image: url("~/static/world-map");
  }
}
</style>
