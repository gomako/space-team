<template>
  <div class="control">
    <label>Boost</label>
    <input v-model="value" type="range" list="tickmarks">
    <datalist id="tickmarks">
      <option value="0" />
      <option value="10" />
      <option value="20" />
      <option value="30" />
      <option value="40" />
      <option value="50" />
      <option value="60" />
      <option value="70" />
      <option value="80" />
      <option value="90" />
      <option value="100" />
    </datalist>
    <span class="value">{{ value }}</span>
    <span class="value target">{{ target }}</span>
  </div>
</template>

<script>
export default {
  name: 'Slider',
  mounted() {
    this.setTarget()
  },
  data() {
    return {
      value: 20,
      target: 0
    }
  },
  watch: {
    value() {
      if(this.value == this.target) {
        this.setTarget();
        this.$emit('targetReached')
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