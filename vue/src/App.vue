<template>
  <div id="app">
    <section id="user-inputs">
      <h1 id="title">MILK TEA PLUS TWO:</h1>
      <h2>Click On Drink Name to Add To Cart</h2>
      <div class="drink-choices">
        <Card
          class="choice"
          v-for="(drinkChoice, index) in drinkChoices"
          @addDrinkList="addDrinkList(index)"
          :key="index"
          :drink="drinkChoice.drink"
          :drinkImage="drinkChoice.drinkImage"
          :description="drinkChoice.description"
          :price="drinkChoice.price"
        />
      </div>
    </section>

    <section id="order-list">
      <h1>Your Order:</h1>
      <Cart
        class="cart"
        v-for="(drinkChoice, index) in order"
        :key="index"
        :order="drinkChoice.drink"
        :price="drinkChoice.price"
      />
      <h2>Subtotal: ${{ subtotal }}</h2>
      <button class="delete-btn" @click="removeLastItem()">
        Delete Last Drink
      </button>
      <button class="delete-btn" @click="removeAllItems()">
        Delete All Drinks
      </button>
    </section>
  </div>
</template>

<script>
import Card from "./components/DrinkCard.vue";
import Cart from "./components/DrinkCart.vue";
export default {
  drink: "App",
  components: {
    Card,
    Cart,
  },
  data() {
    return {
      subtotal: 0,
      selectedDrink: 0,
      drinkChoices: [
        {
          drink: "Original Milk Tea",
          description: "Normal day, normal drink",
          price: 4,
          drinkImage:
            "https://i.etsystatic.com/12249983/r/il/a41a00/2588583785/il_570xN.2588583785_rjoh.jpg",
        },
        {
          drink: "Oolong Milk Tea",
          description:
            "Milk Oolong tea is a Taiwanese tea known for its creamy and buttery taste.",
          price: 4,
          drinkImage:
            "https://sugaryums.co.uk/wp-content/uploads/2022/03/Oolong-Milk-Tea-SugarYums-4.jpg",
        },
        {
          drink: "Thai Milk Tea",
          description:
            "Thai tea is usually made from Ceylon black tea, milk, sugar and spices.",
          price: 4,
          drinkImage:
            "https://theforkedspoon.com/wp-content/uploads/2019/05/Thai-Iced-Tea-Boba-6.jpg",
        },
        {
          drink: "Honey Milk Tea",
          description: "U don't like green tea?",
          price: 4,
          drinkImage:
            "https://shottbeverages.com/wp-content/uploads/2020/06/bubbletea.jpg",
        },
        {
          drink: "Honey Milk Green Tea",
          description: "Aya I guess regular milk green tea is not sweet enough",
          price: 4,
          drinkImage:
            "https://www.honestfoodtalks.com/wp-content/uploads/2021/11/Honeydew-milk-tea-recipe.jpeg",
        },
        {
          drink: "Honey Oolong Milk Tea",
          description: "When the regular oolong milk tea is not sweet enough",
          price: 4,
          drinkImage:
            "https://teabackyard.com/wp-content/uploads/2021/10/oolong-milk-tea.jpg",
        },
        {
          drink: "Coffee Milk Tea",
          description: "For you to pull a semi-all-nighter",
          price: 4,
          drinkImage:
            "https://www.honestfoodtalks.com/wp-content/uploads/2022/07/Coffee-boba-recipe-1.jpeg",
        },
        {
          drink: "Almond Milk Tea",
          description: "I guess you're too good for normal milk.",
          price: 4,
          drinkImage:
            "https://www.honestfoodtalks.com/wp-content/uploads/2022/10/almond-and-black-sugar-milk-tea-boba.jpg",
        },
        {
          drink: "Coconut Milk Tea",
          description: "Eww coconuts",
          price: 4,
          drinkImage:
            "https://images.ctfassets.net/99ef2wobcp71/1n5jCuJVz2IgciuYSgi4Sc/7d359f09849a8a4bfdf468281d8e9dc6/coconut-almond-milk-tea-smoothies-with-boba_edited.jpg",
        },
        {
          drink: "Taro Milk Tea",
          description: "Simple yet delicious",
          price: 3,
          drinkImage:
            "https://www.siftandsimmer.com/wp-content/uploads/2020/12/real-taro-milk-bubble-tea1.jpg",
        },
        {
          drink: "Caramel Frappe",
          description: "Go-to drink in McDonald",
          price: 4,
          drinkImage:
            "https://www.thereciperebel.com/wp-content/uploads/2022/05/caramel-frappuccino-TRR-1200-26-of-26.jpg",
        },
        {
          drink: "Coffee",
          description: "For you to pull an all-nighter",
          price: 2,
          drinkImage:
            "https://www.southsoundtalk.com/wp-content/uploads/2019/11/Coffee-ander-Latte-e1573143205948.jpg",
        },
      ],
      order: [],
      orderPrice: [],
    };
  },
  methods: {
    addDrinkList(index) {
      this.order.push(this.drinkChoices[index]);
      this.orderPrice.push(this.drinkChoices[index].price);
      this.subtotal = this.subtotal + this.drinkChoices[index].price;
    },
    removeLastItem() {
      if (this.order.length !== 0) {
        this.subtotal =
          this.subtotal - this.orderPrice[this.orderPrice.length - 1];
        this.order.pop();
        this.orderPrice.pop();
      }
    },
    removeAllItems() {
      this.order = [];
      this.orderPrice = [];
      this.subtotal = 0;
    },
  },
};
</script>

<style lang="css">
h2 {
  font-size: 20px;
}
#title {
  text-decoration: underline;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  text-align: center;
  color: #25086e;
  display: flex;
  flex-direction: row;
  background-color: #948df5;
}
#user-inputs {
  width: 57vw;
}
.drink-choices {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
}
section {
  display: flex;
  align-items: center;
  flex-direction: column;
}
#order-list {
  border: 10px #09025f solid;
  border-radius: 10px;
  margin: 1rem;
  height: auto;
  background-color: #c7d9ff;
  color: #09025f;
  width: 39vw;
}
.delete-btn {
  margin-bottom: 1rem;
}
</style>
