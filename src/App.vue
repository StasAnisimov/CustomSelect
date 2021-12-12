<template>
  <div id="app">
    <span>{{ selected }}</span>
    <Select :options="options" v-model="selected" multiple/>
  </div>
</template>

<script>
import Select from './components/Select.vue'

export default {
  name: 'App',
  data() {
    return {
      selected: null,
      options: [
        {
          id: 1,
          name: 'Test',
        },
        {
          id: 2,
          name: 'Test1',
        },
        {
          id: 3,
          name: 'Test2',
        },
      ]
    }
  },

  components: {
    Select
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
