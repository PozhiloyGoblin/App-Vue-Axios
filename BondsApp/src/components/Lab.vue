<template>
  <div class="bonds">
    <div class="bonds-item" v-for="value in bonds" :key="value.bonds">
      <div class="bonds_info">
       <div class="bonds_cover">
         {{ value.name }}
       </div>
       <h3 class="bonds_title">
         {{ value.companyName }} 
         <span>{{ value.symbol }}</span>
        </h3>
      </div>
      <span class="bonds_price">{{ value.price }} $</span>
    </div>
  </div>
</template>

<script lang="ts">
import axios from 'axios'
export default {
  name: 'bonds',
  data() {
    return {
      bonds:[],
      errors:[] 
    }
  },
  created() {
    axios.get('https://financialmodelingprep.com/api/v3/quote/BBSI,RL,AAPL,CSCO,ADSK,NFLX,DUK,PEP,PM,JWN,BB,ORCL,GAZP,ROSN,AFLT,MTSS,MAILDR,SBER,VTBR,PFE,FB,GOOG,NVDA,AMD,QIWI,IBM,NIKE,MSFT,V,MCD,TSLA,BA,CAT,DIS,INTC?apikey=91abe6de3810ea4623aa7a29fac42d1f')
    .then(Response => {
      this.bonds = Response.data
      console.log(Response)
    })
    .catch(e =>{
      this.errors.push(e)
    })
  }
}
</script>


