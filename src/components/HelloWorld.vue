<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    
    <BaseList></BaseList>
  </div>
</template>

<script>

import BaseList from './BaseList.vue';
export default {
  name: 'HelloWorld',
  components: {
    BaseList
  },
  props: {
    msg: String
  },
  methods: {

  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
