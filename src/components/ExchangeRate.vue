<template>
  <div class="exchanges">
    <header>
      <h1 class="tittle inter">BTC Exchange Rate</h1>
      <button @click="update()" :style="{ background: 'green'}" class="btn">Update</button>
    </header>
    <table>
      <tr class="tableTitle">
          <th><h2>Currency</h2></th>
          <th><h2>Rate</h2></th>
      </tr>
      <tr v-if="exchange && exchange.bpi">
        <td>USD</td>
        <td>{{ exchange.bpi.USD.rate }}</td>
      </tr>
      <tr v-if="exchange && exchange.bpi">
        <td>EUR</td>
        <td>{{ exchange.bpi.EUR.rate }}</td>
      </tr>
      <tr v-if="exchange && exchange.bpi">
        <td>GBP</td>
        <td>{{ exchange.bpi.GBP.rate }}</td>
      </tr>
      </table>
  </div>
</template>

<script>
export default {
  name: 'ExchangeRate',
  props: [],
  data() {
    return {
      exchange: {},

    };
  },
  methods: {
    async fetchExchange () {
      try{
        const response = await fetch('http://api.coindesk.com/v1/bpi/currentprice.json')
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
}
button {
  margin-left: 30px;
}
.exchanges {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 230px;
  
  margin-bottom: 10px;
  margin-top: 10px;
}
table {
  background: darkolivegreen;
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
}
</style>