<template>
  <div class="hello">
    <h1>Pickaday wrapper</h1>
    <h2>example:</h2>
    <vue-pikaday v-model="date" :options="dateOptions"></vue-pikaday>
  </div>
</template>

<script>
import VuePikaday from './vue-pikaday'

export default {
  name: 'hello',

  data () {
    return {
      date: new Date(),
      dateOptions: {
        format: 'YYYY MM DD dddd'
      }
    }
  },
  components: {
    'vue-pikaday': VuePikaday
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
