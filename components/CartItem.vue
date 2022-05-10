<template>
  <div class="item">
    <div class="item__wrapper">
      <div class="item__header">
        <img class="item__header__image"
             :src="image"
             alt="">
      </div>
      <div class="item__content">
        <div class="item__content__header">
          <h2>{{ title }}</h2>
        </div>
        <div  class="item__content__body">
          <p>{{ text }}</p>
        </div>
        <div  class="item__content__footer">
          <p class="price">{{ price }} <span class="currency">{{ currency }}</span></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CartItem",
  props: {
    image: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      default: ''
    },
    text: {
      type: String,
      default: ''
    },
    price: {
      type: Number,
      default: 0
    },
    currency: {
      type: String,
      default: 'руб.'
    }
  }
}
</script>

<style lang="scss" scoped>

  .item {
    flex-grow: 1;
    min-width: 100px;
    min-height: 200px;
    background: #FFFEFB;
    box-shadow: $block-shadow;
    border-radius: $block-radius;
    margin: 0 8px;
    cursor: pointer;

    &:hover {
      box-shadow: $block-hover-shadow;
    }
    &__header {
      &__image {
        width: 100%;
      }
    }
    &__content {
      padding: 16px 16px 24px 16px;
      &__header {
        h2 {
          font-size: 20px;
          font-weight: 600px;
          line-height: 25px;
          color: $title;
          margin: 0;
          margin-bottom: 16px;
        }
      }
      &__body {
        p {
          font-size: 16px;
          font-height: 20px;
          color: $text;
          margin: 0;
          margin-bottom: 32px;
        }
      }
      &__footer {
        p.price {
          font-size: 24px;
          font-weight: 600;
          line-height: 30px;
          margin: 0;
        }
      }
    }
  }
</style>
