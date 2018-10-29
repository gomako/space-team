<template>
  <div class="control">
    <label>Vent</label>
    <input v-model="value" type="checkbox">
    <span class="value">{{ value }}</span>
    <span class="value target">{{ target }}</span>
  </div>
</template>

<script>
export default {
  name: 'Toggle',
  mounted() {
    this.setTarget()
  },
  data() {
    return {
      value: false,
      target: true
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
      this.target = !this.value;
    }
  }
}
</script>