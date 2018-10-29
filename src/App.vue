<template>
  <div id="app">
    <Game msg="SpaceTeam Thing Here"/>
  </div>
</template>

<script>

/**
 * This is the main entry point for each game, they will contain:
 *  - Display: This will tell you what to do
 *  - Status indicator: How close to explosion!
 *  - Controls: Various controls that you can set to save lé day 
 */

import Game from './components/Game.vue'

export default {
  name: 'app',
  components: {
    Game
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
html, body {
  height: 100%;
  margin: 0;
  padding: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100%;
}
</style>
