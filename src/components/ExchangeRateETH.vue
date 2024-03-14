<template>
  <div class="exchanges">
    <header>
      <h1 class="tittle inter">Ξ Etherium</h1>
      <button @click="update()" :style="{ background: 'green'}" class="btn">Update</button>
    </header>
    <table>
      <tr class="tableTitle">
          <th><h2>Currency</h2></th>
          <th><h2>Rate</h2></th>
      </tr>
      <tr v-if="exchange && exchange.ETH">
        <td>USD</td>
        <td>{{ exchange.ETH.USD }}</td>
      </tr>
      <tr v-if="exchange && exchange.ETH">
        <td>EUR</td>
        <td>{{ exchange.ETH.EUR }}</td>
      </tr>
      </table>
  </div>
</template>

<script>
export default {
  name: 'ExchangeRateETH',
  props: [],
  data() {
    return {
      exchange: {},

    };
  },
  methods: {
    async fetchExchange () {
      try{
        const response = await fetch('https://min-api.cryptocompare.com/data/pricemulti?fsyms=ETH&tsyms=USD,EUR&api_key={f3d184a97bd0fe5987fc2520bb7111557345e7437308a75fcf20d7ee63c4428d}')
        const data = await response.json()
        return data
      }
      catch (error) {
        console.log(error)
      }
    },
    async update () {
      this.exchange = await this.fetchExchange()
    }
  },
  async created() {
    this.update()
  }
}
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
.title {
  font-size: 32px;
  text-align: center;
  padding-right: 15px;
  }
.inter {
  font-family: "Inter", sans-serif;
  font-optical-sizing: auto;
  font-weight: 700;
  font-style: normal;
  font-variation-settings:
  "slnt" 0;
  color: white;
}
button {
  margin-left: 30px;
}
.exchanges {
  background: #284875;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 230px;
  border-radius: 8px;
  padding: 20px 30px;
  margin-bottom: 10px;
  margin-top: 10px;
  
}
table {
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 8px;
  min-width: 440px;
}
td{
  background: #404741;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 8px;
}
td:hover{
  background: #374039;
}
th{
  background: #2b302c;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 8px;
  color: white;
}
</style>
