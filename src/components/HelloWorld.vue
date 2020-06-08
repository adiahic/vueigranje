<template>
  <div>
   
    <h2>{{msg}}</h2>
      
      <button class="btn btn-primary" @click="uzmi1()">Hoću novi</button>
      <h1 >  {{koktel}}    </h1>
      
      <img :src="slika" alt="HANGOUT PHOTO">
  </div>
</template>

<script>
const axios = require('axios').default;

export default {

  
  data : function () {
		return {
      koktel: 'koktel neki ba',
      slika:'',
      }
		},
mounted() {
    axios.get('https://www.thecocktaildb.com/api/json/v1/1/random.php')
      .then((response) => {
          this.koktel = response.data.drinks[0].strDrink;
          this.slika = response.data.drinks[0].strDrinkThumb;
        console.log(response.data.drinks[0].strDrink)
      });
  },

  methods: {
   uzmi1: function uzmi ()
       {axios.get('https://www.thecocktaildb.com/api/json/v1/1/random.php')
      .then((response) => {
          this.koktel = response.data.drinks[0].strDrink;
           this.slika = response.data.drinks[0].strDrinkThumb;
        console.log(response.data.drinks[0].strDrink)
      })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
  .then(function () {
    // always executed
  });

       }
   },
  
    
    


  props: {
    msg: String
  }
};
 
</script>

<style>
img{
  height: 100px;
  width: 100px;
}
</style>






















































































































