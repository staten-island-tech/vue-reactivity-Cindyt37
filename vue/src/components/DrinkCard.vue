<template>
  <div class="choice">
    <button class="drink" @click="$emit('addDrinkList')">
      {{ drink }}. . . . ${{ price }}
    </button>
    <img class="image" :src="drinkImage" :alt="description" />
    <h1 class="description">{{ description }}</h1>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    drink: String,
    price: Number,
    drinkImage: String,
    description: String,
  },
};
</script>

<style>
.image {
  height: 10rem;
  object-fit: cover;
  display: block;
}
.description {
  font-size: 12px;
  align-content: center;
}
.choice {
  display: flex;
  flex-direction: column;
  margin-left: 20px;
  width: 12.7vw;
}
</style>
