<template>
  <input type="text" ref="input" v-bind:value="value">
</template>

<script>
import Pikaday from 'pikaday'
import 'pikaday/css/pikaday.css'

export default {
  name: 'vue-pikaday',

  props: ['value', 'options'],

  mounted () {
    const vm = this

    const pikdayOptions = Object.assign({
      field: this.$refs.input,
      onSelect () {
        vm.$emit('input', this.toString())
      }
    }, this.options)

    this.picker = new Pikaday(pikdayOptions)
  },

  updated () {
    this.picker.setDate(this.value)
  },

  beforeDestroy () {
    this.picker.destroy()
  }
}
</script>

<style>

</style>
