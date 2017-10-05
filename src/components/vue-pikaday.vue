<template>
  <input type="text" ref="input" v-once :value="formattedDate">
</template>

<script>
import moment from 'moment'
import Pikaday from 'pikaday'
import 'pikaday/css/pikaday.css'

export default {
  name: 'vue-pikaday',

  props: ['value', 'options'],

  computed: {
    formattedDate () {
      const format = this.options && this.options.format

      return moment(this.value).format(format)
    }
  },

  mounted () {
    const vm = this

    const pikdayOptions = Object.assign({
      field: this.$refs.input,
      onSelect () {
        vm.$emit('input', this.getDate())
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
