<template>
  <div class="game">
    <h1>{{ msg }} {{ score }}</h1>
    <div v-if="score < maxScore" class="controls">
      <Slider @targetReached="score++"></Slider>
      <Toggle @targetReached="score++"></Toggle>
    </div>
    <div v-else>
      <h1>YOU WIN!</h1>
    </div>
  </div>
</template>

<script>

import Slider from './controls/Slider.vue'
import Toggle from './controls/Toggle.vue'

export default {
  name: 'Game',
  components: {
    Slider,
    Toggle
  },
  mounted() {
    this.setTarget()
  },
  props: {
    msg: String
  },
  data() {
    return {
      value: 20,
      target: 0,
      score: 0,
      maxScore: 10
    }
  },
  watch: {
    value() {
      if(this.value == this.target) {
        this.setTarget();
        this.score++;
      }
    }
  },
  methods: {
    setTarget() {
      this.target = Math.floor(1 + Math.random()*10)*10;
    }
  }
}
</script>

<style>
.game {
  display: flex;
  align-items: center;
  flex-wrap: nowrap;
  flex-direction: column;
  background: #ccc;
  height: 100%;
  padding: 1rem;
}
.controls {
  background: #999;
  padding: 1rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
  box-shadow: 0 2px 2px rgba(0,0,0,0.5);
}
.control {
  height: 200px;
  width: 200px;
  padding: 1rem;
  margin-right: 1rem;
  background: #eee;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-content: space-between;
}
.control:last-child {
  margin-right:0;
}
.control label, 
.control input {
  text-align: center;
  flex: 1;
}
.control input {
  padding: 1rem 0;
}
.control .value {
  background: #111;
  color: white;
  font-family: monospace;
  display: block;
  padding: .4rem;
  text-align:center;
}
.control .value.target {
  color: green;
}
</style>
