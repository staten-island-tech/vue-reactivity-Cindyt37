<template>
    <div class="card">
        <img v-bind:src="image" alt="">
        <h1 class="card-title">{{title}}</h1>
        <p class="card-description">{{description}}</p>
        <div class="card-line">
            <h3 class="card-cost">${{cost}}.00</h3>
<!-- <Button @click="$emit('addItemToCart')" > add to cart </Button> -->
        </div>
        
   
    </div>
</template>

<script>
export default {
    name:"Card", 
    props:{
       title:String,
       image:String,
       cost: String,
       description: String,
   },

};
   
</script>
<style >
.card{
    width: 30rem;
    height: 30rem;
    margin: 4rem auto;
   
}
img{
    width: 14rem;
    height: 18rem;
    object-fit: cover;
    border: solid rgb(41,43,131) 3px;
}
.card-title, .card-cost
{
    margin: 0rem 0rem;
    text-align: left;
}
.card-cost{
    margin-top: .7rem;
}
 .card-description{
    margin: 1rem 0rem 2rem 0rem;
     text-align: left;
 }
 .card-line{
  display: flex;
  justify-content: space-between;
 }


</style>
