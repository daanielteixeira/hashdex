const { get } = require("core-js/core/dict")


<template>

  <div class="bg-purple-400 p-5">
    <h1 class = "font-semibold text-3xl" style="text-align:center">Cotação Monetária - Daniel Teixeira</h1>
    <div class="m-7 mx-auto w-1/2 bg-purple-300 pt-24 pl-14 pb-24 pr-24">
    
    <table class="rounded-2xl ml-72" v-for="moeda in moedas">
      <h2 class="font-bold">{{ moeda.code }} / {{ moeda_par }} - ${{ moeda.bid }}</h2>
    </table>
    <form>
      <p class="mt-52">Adicione uma nova moeda: <br>
        <select class ="w-48 h-10 rounded-lg border-2" id="add_coins" @change="uploadCoins" >
          <option value=""></option>
          <option value="eth">ETH / USD</option>
          <option value="ltc">LTC / USD</option>
          <option value="doge">DOGE / USD</option>
          <option value="eur">EUR / USD</option>
          <option value="egp">EGP / USD</option>
          <option value="cad">CAD / USD</option>
          <option value="gpb">GBP / USD</option>
          <option value="ars">ARS / USD</option>
          <option value="jpy">JPY / USD</option>
          <option value="uyu">UYU / USD</option>
          <option value="chf">CHF / USD</option>
          <option value="nzd">NZD / USD</option>
          <option value="aud">AUD / USD</option>
        </select>        
      </p>
      <input type="button" value ="Adicionar" class="mt-2 p-1.5 rounded-lg" style="margin-left:113px" @click="loadCoins" id="load_coin"></input>
      

    </form>
    </div>
   
    
  </div>
</template>
<script>

export default{
    data(){
      return{
        
        moedas:[],
        moeda_par: "USD",
        url: "https://economia.awesomeapi.com.br/last/BTC-USD"
      }
    },
    
    methods:{
      
      loadCoins() {
        setInterval(() => {
          document.getElementById("load_coin").click();
        }, 30000);
        this.$axios
        
        .$get(this.url)
        .then((response) => {
          this.moedas = response
        })
        .catch(() => {
          console.log("ERRO")
        })
        
      },
      uploadCoins:function upload(event){
        
        var res = event.target.value
        if(res === 'ltc'){
          this.url += ",LTC-USD"
        }
        else if(res === 'eth'){
          this.url += ",ETH-USD"
        }
        else if(res === 'doge'){
          this.url += ",DOGE-USD"
        }
        else if(res === 'eur'){
          this.url += ",EUR-USD"
        }
        else if(res === 'egp'){
          this.url += ",EGP-USD"
        }
        else if(res === 'cad'){
          this.url += ",CAD-USD"
        }
        else if(res === 'gbp'){
          this.url += ",GBP-USD"
        }
        else if(res === 'ars'){
          this.url += ",ARS-USD"
        }
        else if(res === 'jpy'){
          this.url += ",JPY-USD"
        }
        else if(res === 'uyu'){
          this.url += ",UYU-USD"
        }
        else if(res === 'chf'){
          this.url += ",CHF-USD"
        }
        else if(res === 'nzd'){
          this.url += ",NZD-USD"
        }
        else if(res === 'aud'){
          this.url += ",AUD-USD"
        }   
        
      }
    }
  }

  
    
   
   
      
    
  
    
  
  
</script>
