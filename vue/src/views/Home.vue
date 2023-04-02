<template>
  <html lang="en">
    <title>hi</title>
    
    <div class="home">
      <Button class="cart-button" @click="isShow = !isShow"></Button>
      <button class="cart-button" @click="isShow = !isShow">
        Cart
        <img
          class="icon"
          src="https://cdn-icons-png.flaticon.com/512/263/263142.png"
          alt=""
        />
      </button>
      <h1 id="length">{{ cart.length }} in</h1>
      <div class="cart" v-show="isShow">
        <Cart
          class="carty"
          v-for="(product, index) in cart"
          @removeItemFromCart="removeItemFromCart(product)"
          :key="index"
          :image="product.img"
          :title="product.name"
          :cost="product.cost"
        />
        <h3 >total cost: ${{total}}.00</h3>
      </div>

      <div></div>

      <div class="cards">
        <Card
          class="cardy"
          v-for="(product, index) in products"
          @addItemToCart="addItemToCart(product)"
          :key="index"
          :title="product.name"
          :description="product.description"
          :image="product.img"
          :cost="product.cost"
        />
      </div>
    </div>
  </html>
</template>

<script>
// @ is an alias to /src
import Button from "../components/Button.vue";
import Card from "../components/Card.vue";
import Cart from "../components/Cart.vue";
export default {
  name: "Home",
  components: {
    Button,
    Card,
    Cart,
  },
  data() {
    return {
      selected: "",
      isShow: false,
      cart: [],
      products: [
        {
          quantity: 1,
          name: "Original Milk Tea",
          description: "Normal day, normal drink",
          cost: 4,
          img: "https://i.etsystatic.com/12249983/r/il/a41a00/2588583785/il_570xN.2588583785_rjoh.jpg",
        },
        {
          quantity: 1,
          name: "Oolong Milk Tea",
          description: "Milk Oolong tea is a Taiwanese tea known for its creamy and buttery taste.",
          cost: 4,
          img: "https://sugaryums.co.uk/wp-content/uploads/2022/03/Oolong-Milk-Tea-SugarYums-4.jpg",
        },
        {
          quantity: 1,
          name: "Thai Milk Tea",
          description:
            "Thai tea is usually made from Ceylon black tea, milk, sugar and spices (typically cardamom and star anise).",
          cost: 4,
          img: "https://theforkedspoon.com/wp-content/uploads/2019/05/Thai-Iced-Tea-Boba-6.jpg",
        },
        {
          quantity: 1,
          name: "Honey Milk Tea",
          description: "When you don't like green tea",
          cost: 4,
          img: "https://shottbeverages.com/wp-content/uploads/2020/06/bubbletea.jpg",
        },
        {
          quantity: 1,
          name: "Honey Milk Green Tea",
          description: "When the regular milk green tea is not sweet enough",
          cost: 4,
          img: "https://www.honestfoodtalks.com/wp-content/uploads/2021/11/Honeydew-milk-tea-recipe.jpeg",
        },
        {
          quantity: 1,
          name: "Honey Oolong Milk Tea",
          description: "When the regular oolong milk tea is not sweet enough",
          cost: 6,
          img: "https://teabackyard.com/wp-content/uploads/2021/10/oolong-milk-tea.jpg",
        },
        {
          quantity: 1,
          name: "Coffee Milk Tea",
          description: "For you to pull a semi-all-nighter",
          cost: 8,
          img: "https://www.honestfoodtalks.com/wp-content/uploads/2022/07/Coffee-boba-recipe-1.jpeg",
        },
        {
          quantity: 1,
          name: "Almond Milk Tea",
          description: "Almond milk tea is made of almond milk, any black tea of your choice, and a sweetener or syrup to enhance the overall flavour and deliciousness.",
          cost: 2,
          img: "https://www.honestfoodtalks.com/wp-content/uploads/2022/10/almond-and-black-sugar-milk-tea-boba.jpg",
        },
        {
          quantity: 1,
          name: "Coconut Milk Tea",
          description: "Eww coconuts",
          cost: 24,
          img: "https://images.ctfassets.net/99ef2wobcp71/1n5jCuJVz2IgciuYSgi4Sc/7d359f09849a8a4bfdf468281d8e9dc6/coconut-almond-milk-tea-smoothies-with-boba_edited.jpg",
        },
        {
          quantity: 1,
          name: "Honeydew Milk Green Tea",
          description: "This cooling beverage is made up of honey melon juice, plant-based milk and topped with cooked tapioca pearls.",
          cost: 11,
          img: "https://www.honestfoodtalks.com/wp-content/uploads/2021/11/Honeydew-milk-tea-recipe.jpeg",
        },
        {
          quantity: 1,
          name: "Taro Milk Tea",
          description: "Simple yet delicious",
          cost: 3,
          img: "https://www.siftandsimmer.com/wp-content/uploads/2020/12/real-taro-milk-bubble-tea1.jpg",
        },
        {
          quantity: 1,
          name: "Caramel Frappe",
          description: "Go-to drink in McDonald",
          cost: 7300,
          img: "https://www.thereciperebel.com/wp-content/uploads/2022/05/caramel-frappuccino-TRR-1200-26-of-26.jpg",
        },

        {
          quantity: 1,
          name: "Coffee",
          description:
            "For you to pull an all-nighter",
          cost: 5,
          img: "https://www.southsoundtalk.com/wp-content/uploads/2019/11/Coffee-ander-Latte-e1573143205948.jpg",
        },
      ],
    };
  },
  computed: {
    total() {
      return this.cart.reduce((acc, item) => acc + item.cost, 0);
    },
  },
  methods: {
    authState: function () {
      if (this.loggedIn === false) {
        this.loggedIn = true;
      } else {
        this.loggedIn = false;
      }
    },
    showState: function () {
      if (this.isShow === false) {
        this.isShow = true;
      } else {
        this.isShow = false;
      }
    },
    addItemToCart(product) {
      /*   let found = this.cart.find(product => product.name ==product.name);
console.log(this.cart);
     if(found){
found.quantity++;
     }else{
this.cart.push(product);
     } */
      this.cart.push(product);
    },
    removeItemFromCart(product) {
      this.cart.splice(this.cart.indexOf(product), 1);
    },
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Amiko:wght@400;700&display=swap");
body {
  background-color: rgb(232, 226, 215);
  font-family: "Amiko", sans-serif;
}
h1 {
  color: rgb(41, 43, 131);
}

.cards {
  display: flex;
  flex-direction: row;
  flex-flow: wrap;
  justify-content: center;
  margin: 7rem;
  margin-top: 0rem;
}
.cardy {
  margin: 3rem 4rem;
  height: 30rem;
  width: 14rem;
}
.icon {
  width: 1.7rem;
  height: 1.7rem;
  border: none;
}
.cart {
  text-align: center;
}
.cart-button1 {
  position: absolute;
  right: 0px;
  padding: 10px;
  margin-right: 7rem;
  color: rgb(232, 226, 215);
  background-color: rgb(232, 226, 215);
}
.cart-button1:hover,
.cart-button1:active {
  color: rgb(232, 226, 215);
  background-color: rgb(232, 226, 215);
}
.cart-button {
  position: absolute;
  right: 0px;
  padding: 10px;
  margin-right: 9rem;
  margin-top: 0rem;
}

Button {
  justify-content: right;
}
p {
  text-align: center;
  margin: 2rem;
}
#length {
  text-align: right;
  margin-right: 18rem;
  margin-top: 0rem;
}
</style>
