<template>
  <div id="select-div">
    <div><input type="text" v-model="search">
      <button @click="visible = !visible">{{ visible ? 'Hide items' : 'Show items' }}</button>
    </div>
    <div></div>
    <div v-if="visible">
      <ul>
        <li
            v-for="(option, index) of filteredOptions" :key="index"
        >
          <input v-model="selected" :id="index" :type="multiple ? 'checkbox' : 'radio'" :value="option.id">
          <label :for="index">{{ option.name }}</label>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    filteredOptions() {
      return this.options.filter(item => {
        return item.name.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },

  watch: {
    selected() {
      this.$emit('input', this.selected)
    }
  },

  props: {
    options: {
      type: Array,
      required: true
    },
    multiple: {
      type: Boolean,
      default: false
    }
  },

  data() {
    return {
      visible: false,
      search: '',
      selected: []
    }
  }
}
</script>

<style scoped>
</style>
