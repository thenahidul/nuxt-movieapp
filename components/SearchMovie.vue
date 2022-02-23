<template>
  <input
    type="text"
    :value="value"
    @input="$emit('input', $event.target.value)"
  />
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: '',
    },
  },
}
</script>

<style lang="scss" scoped>
input {
  border: none;
  padding: 10px 15px;
  width: 180px;
  border-radius: 5px;
  margin-right: 5px;
}
</style>
