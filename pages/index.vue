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
            <form class="content-body__sidebar__wrapper__form"
                  v-on:submit.prevent="addNewCartItem">
              <label for="name-item">Наименование товара</label>
              <input
                v-model="itemName"
                id="name-item"
                placeholder="Введите наименование товара"
              >
              <label for="text-item">Описание товара</label>
              <textarea
                v-model="itemText"
                id="text-item"
                placeholder="Введите описание товара"
              ></textarea>
              <label for="link-item">Ссылка на изображение товара</label>
              <input
                v-model="itemLink"
                id="link-item"
                placeholder="Введите ссылку"
              >
              <label for="price-item">Цена товара</label>
              <input
                v-model="itemPrice"
                id="price-item"
                placeholder="Введите цену"
              >
              <button>Добавить</button>
            </form>
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
    addNewCartItem: function () {
      this.CartItemList.push({
        image: '/_nuxt/static/images/image.jpg',
        title: this.itemName,
        text: this.itemText,
        price: this.itemPrice,
        currency: 'руб.',
      })
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
    justify-content: space-between;
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
      box-sizing:border-box;
      //flex-grow: 1;
      flex-shrink: 0;
      padding: 0 8px;
      &__wrapper {
        padding: 24px;
        background: #FFFEFB;
        box-shadow: $block-shadow;
        border-radius: $block-radius;
        &__form {
          display: flex;
          flex-direction: column;
          label {
            font-family: $default-font;
            font-size: 10px;
            line-height: 13px;
            letter-spacing: -0.02em;
            color: $label;
            margin-bottom: 4px;
          }
          input {
            font-family: $default-font;
            width: auto;
            margin-bottom: 16px;
            padding: 10px 16px 11px 16px;
            background: #FFFEFB;
            box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
            border-radius: 4px;
            border: none;
            ::placeholder {
              font-family: $default-font;
              font-size: 12px;
              line-height: 15px;
              color: $disabledText;
            }
          }
          textarea {
            font-family: $default-font;
            height: 108px;
            resize: none;
            rows: 5;
            margin-bottom: 16px;
            padding: 10px 16px 11px 16px;
            background: #FFFEFB;
            box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
            border-radius: 4px;
            border: none;
          }
          button {
            background: $disabled;
            border-radius: 10px;
            border: none;
            padding: 10px 10px 11px 10px;
            font-family: 'Inter';
            font-style: normal;
            font-weight: 600;
            font-size: 12px;
            line-height: 15px;
            text-align: center;
            letter-spacing: -0.02em;
            color: $disabledText;
            &:hover {
              box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.3);
            }
          }
        }
      }
    }
    &__main {
      width: 75%;
      flex-grow: 3;
      display: flex;
      justify-content: flex-start;
      flex-wrap: wrap;
    }

  }

}

</style>
