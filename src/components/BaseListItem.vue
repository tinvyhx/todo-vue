<template>
  <li v-bind:style="bgColor">
    {{todo.text}}<button @click="$emit('remove',todo.id)">x</button>
  </li>
</template>

<script>
export default {
  name: 'BaseListItem',
  props: {
    todo: {
      type: Object,
      required: true
    }
  },

  computed: {

    bgColor () {
      const r = this.random255(),
        g = this.random255(),
        b = this.random255()
      return {
        backgroundColor: `rgb(${r},${g},${b})`,
        color: `rgb(${255 - r},${255 - g},${255 - b})`
      }
    }
  },
  methods: {
    random255 () {
      return Math.random() * 255
    }
  },
}
</script>

<style scoped>
li {
  position: relative;
  text-align: left;
  font-size: 35px;
  margin: 10px;
  text-indent: 10px;
  border-radius: 4px;
}
li button {
  width: 20px;
  height: 20px;

  position: absolute;
  right: 10px;
  margin-top: 10px;
  border: none;
  background-color: rgba(104, 16, 16, 0.178);
}
</style>