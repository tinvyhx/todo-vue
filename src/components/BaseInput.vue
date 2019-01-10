<template>

  <input
    type="text"
    placeholder="to be done"
    :value="value"
    v-on="listeners"
  >

</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: ''
    }
  },
  name: 'BaseInput',
  computed: {
    listeners () {

      return {
        ...this.$listeners,
        input: event => this.$emit('input', event.target.value)
      }
    }
  },
}
</script>


<style scoped>
input:focus{
    outline-style: none
}
input {
  height: 40px;
  width: 80%;
  border: 1px solid #f78;
  padding: 10px;
  font-size: 25px;
  line-height: 25px;
  border-radius: 10px;
}
</style>