<template>
  <div id="app">
    <Navigation/>
    <div class="row between-md">
      <div class="col-md-5 col-sm-12 col-xs-12">
        <div class="hero">
          <h1>
            Beautifull and User-friendly currency exchange!
          </h1>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Facere nemo obcaecati accusamus nobis quae, ipsam voluptatem accusantium cum odit iste, dolore temporibus explicabo dolorem soluta laboriosam omnis pariatur veritatis cupiditate porro vero. Laudantium, voluptate unde.
          </p>
          <div class="exchange-form">
            <div class="input-currency">
              <img src="http://cdn.shopify.com/s/files/1/1061/1924/products/Money_Bag_Emoji_grande.png?v=1571606064" alt="">
              <input v-model="currentCurrency" type="text" placeholder="Type currency like USD">
            </div>
            <a href="#" v-on:click="getExchangeData" class="btn">Get exchange</a>
          </div>
        </div>
      </div>

      <div class="col-md-6 col-sm-12 col-xs-12">
        <div class="currency-exchange">
          <div class="results">
            <div class="result-card" v-for="(rate,keyJSON) in rates" :key="keyJSON">
              <h3>{{keyJSON + ':'}}</h3>
              <h4>{{rate}}</h4>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import Navigation  from './components/Navigation.vue'

export default {
  name: 'App',
  components: {
    Navigation
  },
  data(){
    return{
      currentCurrency:"",
      rates:{

      }
    }
  },
  methods:{
    getExchangeData:function(){
      console.log("Request");
      let baseURL = 'https://api.exchangerate.host/latest?';
      let baseCurrency = 'base='+this.currentCurrency ;
      let symbols = "&symbols=USD,EUR,UAH,BTC"
      axios
        .get(baseURL+baseCurrency+symbols)
        .then((response) => {
          console.log(response.data.rates);
          this.rates = response.data.rates;
        });
      }
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Jost:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

  *{
    font-family: Jost;
    margin: 0px;
  }



  .currency-exchange{
    border-radius: 32px 32px 0px 0px;
    height: calc(100vh - 128px);
    box-sizing: border-box;
    background: #ff7418;
    margin-top: 64px;
    overflow: hidden;
  }

  body{
    padding: 32px 64px;
    padding-bottom: 0px;
  }

  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    
  }

  a{
    
    font-size: 20px;
    text-decoration: none;
    color: #111111;
    line-height: 100%;
    font-weight: 500;
  }

  p{
    font-size: 20px;
    font-weight: 300;
    color: #303030;
    margin-bottom: 16px;
  }

  h1{
    font-size: 64px;
    line-height: 110%;
    margin-bottom: 32px;
    margin-top: 48px;
  }

  h3{
    font-size: 32px;
    font-weight: 300;
    margin-bottom: 24px;
    margin-top: 24px;
  }

  .hero p{
    margin-bottom: 48px;
  }

  .hero{
    margin-top: 164px;
  }

  a.btn{
    padding: 16px 24px;
    background: #ff7418;
    color: white;
    border-radius: 16px;
    box-sizing: border-box;
    min-width: 100px;
    text-align: center;
  }

  a.btn.btn-outline{
    color: #ff7418;
    border: 2px solid #ff7418;
    background: none;
    box-sizing: border-box;
  }

  .input-currency{
    padding: 16px 16px;
    box-sizing: border-box;
    border-radius: 16px;
    border: #111111 2px solid;
    display: flex;
    align-items: center;
    position: relative;
    flex:1;
  }

  .input-currency img{
    height: 32px;
    width: 32px;
    margin-right: 12px;
  }

  .input-currency input{
    background: none;
    border: none;
    font-size: 20px;
    font-weight: 400;
    color: #111111;
    outline: none;
    width: 100%;
  }
  
  .exchange-form{
    display: flex;
    gap:12px;
  }

  .exchange-form a{
    line-height: 150%;
  }

  .results{
    display: grid; 
    grid-template-columns: 1fr 1fr; 
    grid-template-rows: 1fr 1fr; 
    gap: 0px 0px; 
    grid-template-areas: 
      ". ."
      ". ."; 
    height: 100%;
  }

  .result-card{
    outline: 1px solid #111111; 
    padding: 32px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  .result-card h3{
    color:#111111;
    font-size: 48px;
    font-weight: 200;
  }
  .result-card h4{
    color:#111111;
    font-size: 24px;
    font-weight: 400;
  }

  @media screen and (max-width: 1440px) {
    body{
      height: 100vh;
      overflow: hidden;
    }

    .hero p{
      margin-bottom: 48px;
    }

    .hero{
      margin-top: 164px;
    }

    p,a,span,input{
      font-size: 20px;
    }

    h1{
      font-size: 64px;
    }

  }

  @media screen and (max-width: 1050px) {
    body{
      height: 100vh;
      overflow: hidden;
    }

    .hero p{
      margin-bottom: 32px;
    }

    .hero{
      margin-top: 32px;
    }

    p,a,span,input{
      font-size: 16px;
    }

    h1{
      font-size: 48px;
    }

  }

  @media screen and (max-width: 770px) {
    body{
      height: auto;
      overflow: auto;
    }

    .nav{
      display: none;
    } 

    .hero p{
      margin-bottom: 32px;
    }

    .hero{
      margin-top: 32px;
    }

    p,a,span,input{
      font-size: 16px;
    }

    h1{
      font-size: 48px;
    }

  }

  @media screen and (max-width: 400px) {
    body{
      padding: 16px;
      padding-bottom: 0px;
    }

    .nav{
      display: none;
    } 

    .hero p{
      margin-bottom: 32px;
    }

    .hero{
      margin-top: 32px;
    }

    p,a,span,input{
      font-size: 16px;
    }

    h1{
      font-size: 48px;
    }

    .exchange-form{
      flex-direction: column;
    }

  }
</style>
