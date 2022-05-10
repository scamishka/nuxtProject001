<template>
  <div class="body-block">
    <div class="body-block__container">
      <HeaderTitle/>
      <ContentBlock/>
    </div>
  </div>
</template>

<script>
import HeaderTitle from "../components/HeaderTitle";
import ContentBlock from "../components/ContentBlock";
export default {
  name: 'IndexPage',
  components: {ContentBlock, HeaderTitle}
}
</script>

<style lang="scss" scoped>
.body-block {
  width: 100%;
  display: flex;
  justify-content: center;
  &__container {
    width: 100%;
    max-width: 1500px;
    display: flex;
    flex-direction: column;

  }
}

</style>
