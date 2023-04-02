<template>
    <div class="cart">
        <div class="card">
            <div class="card-image">
                <img v-bind:src="image" alt="">
            </div>
       <div class="card-text">
        <h2 class="card-title">{{title}}</h2>
        <h3 class="card-cost">${{cost}}.00</h3>
        </div>
        <div class="cardbutton">
<Button @click="$emit('removeItemFromCart')" > x </Button>
       </div>
    </div>
    </div>
</template>
<script>
export default {
    name:"Cart",
    props:{
       title:String,
       image:String,
       cost: String,
   },
   methods:{
       
   }

}
</script>
<style scoped >
.card{
    display: grid;
    grid-template-columns: 1fr 2fr 1fr ;
    grid-column-gap: 2rem;
    

    
}
.card{
    width: 30rem;
    height: 7.8rem;
    background-color: white;
    margin: 4rem auto;
    border: solid rgb(41,43,131) 3px;
   
}
img{
    width: 7.5rem;
    height: 7.5rem;
    object-fit: cover;
 
}
.card-title
{
    margin-top: 1rem;
    text-align: left;
}
 .card-description{
     margin:  0rem 0rem 0rem 1rem;
 }

Button{
    margin-top: 2.5rem;
    width: 3rem;
    height: 3rem;
}

</style>

