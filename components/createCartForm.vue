<template>
    <form @submit.prevent="onSubmit">
      <div>
        <BaseInput
          v-bind:id="$data.dataForm.id"
          v-bind:label="$data.dataForm.label"
          v-bind:placeholder="$data.dataForm.placeholder"
          v-bind:required="$data.dataForm.required"
        />
      </div>
      <input type="submit" value="submit">
    </form>
</template>

<script>
import BaseInput from "./baseInput";
export default {
  name: "createCartForm",
  components: {BaseInput},
  data() {
    return {
      nameItem: null,
      dataForm: [
        {
          id: 'nameItem',
          label: 'Наименование товара',
          placeholder: 'Введите наименование товара',
          required: true
        }
      ]
    }
  },
  methods: {
    onSubmit() {
      let productItem = {
        name: this.name,
      }
      this.$emit('item-submitted', productItem)
      this.name = null
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
