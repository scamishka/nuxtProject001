<template>
  <label :for="id">
    {{ label }}
    <input
      :id="id"
      :placeholder="placeholder"
      :required="required"
    >
  </label>
</template>

<script>
export default {
  name: "baseInput",
  inheritAttrs: false,
  props: {
    id: {
      type: String,
      default: ''
    },
    label: {
      type: String,
      default: ''
    },
    placeholder: {
      type: String,
      default: ''
    },
    required: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped>

</style>
