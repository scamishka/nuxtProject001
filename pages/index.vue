<template>
  <div class="body-block">
    <div class="body-block__container">
      <div class="content-header">
        <h1>Добавление товара</h1>
        <select name="sort">
          <option>По умолчанию</option>
        </select>
      </div>
      <div class="content-body">
        <div class="content-body__sidebar">
          <div class="content-body__sidebar__wrapper">
            <input type="text" v-model="newPhone" />
            <button v-on:click="phones.push(newPhone)">Добавить</button>
          </div>
        </div>
        <div class="content-body__main">
          <CartItem v-for="(item, key) in CartItemList"
                    v-bind:key="key"
                    v-bind:image="item.image"
                    v-bind:title="item.title"
                    v-bind:text="item.text"
                    v-bind:price="item.price"
                    v-bind:currency="item.currency"
                    :class="HoverClass"
                    v-on:remove="CartItemList.splice(key, 1)"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CartItem from "../components/CartItem";
import CreateCartForm from "../components/createCartForm";
export default {
  name: 'IndexPage',
  components: {CartItem},
  data() {
    return {
      HoverClass: '',
      newItem: {},
      CartItemList: [
        {
          image: require('@/static/images/image.jpg'),
          title: 'Наименование товара',
          text: 'Довольно-таки интересное описание товара в несколько строк.' +
            'Довольно-таки интересное описание товара в несколько строк',
          price: 10000,
          currency: 'руб.'
        },
        {
          image: require('@/static/images/image.jpg'),
          title: 'Наименование товара',
          text: 'Довольно-таки интересное описание товара в несколько строк.' +
            'Довольно-таки интересное описание товара в несколько строк',
          price: 10000,
          currency: 'руб.'
        },
        {
          image: require('@/static/images/image.jpg'),
          title: 'Наименование товара',
          text: 'Довольно-таки интересное описание товара в несколько строк.' +
            'Довольно-таки интересное описание товара в несколько строк',
          price: 10000,
          currency: 'руб.'
        }
      ],
      errors: [],
      name: null,
      age: null,
      movie: null
    }
  },
  methods: {
    checkForm: function (e) {
      if (this.name && this.age) {
        return true;
      }

      this.errors = [];

      if (!this.name) {
        this.errors.push('Требуется указать имя.');
      }
      if (!this.age) {
        this.errors.push('Требуется указать возраст.');
      }

      e.preventDefault();
    },
    onHover() {
      console.log('hover');
      this.HoverClass = 'hover'
    },
    leaveHover() {
      console.log('off hover');
      this.HoverClass = '';
    },
    addItem(productItem) {
      this.items.push(productItem)
    }
  }
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
  .content-header {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin: 0 8px;
    h1  {
      font-weight: 600;
      font-size: 28px;
      line-height: 35px;
    }
  }
  .content-body {
    display: flex;
    flex-flow: row wrap;
    &__sidebar {
      width: 25%;
      flex-grow: 1;
      flex-shrink: 0;
      background: #FFFEFB;
      box-shadow: $block-shadow;
      border-radius: $block-radius;
      &__wrapper {
        padding: 24px;
        margin: 0 8px;
      }
    }
    &__main {
      width: 75%;
      flex-grow: 3;
      display: flex;
      justify-content: space-between;
    }

  }

}

</style>
