<template>
  <header>
    <div class="header_content">
      <h1>Добавление товара</h1>
      <select name="sort">
        <option>По умолчанию</option>
      </select>
    </div>
  </header>
</template>

<script>
export default {
  name: "HeaderTitle"
}
</script>

<style lang="scss" scoped>
.header_content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  h1  {
    font-weight: 600;
    font-size: 28px;
    line-height: 35px;
  }
}

</style>
