<template>
  <div class="container">
    <h1 class="inter">Exchange Rates 📉</h1>

    <ExchangeRateETH />
    <ExchangeRateBTC />
  </div>
</template>

<script>
import ExchangeRateBTC from '@/components/ExchangeRateBTC.vue';
import ExchangeRateETH from '@/components/ExchangeRateETH.vue';


export default {
  name: 'ExchangeView',
  components: {
    ExchangeRateBTC,
    ExchangeRateETH
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');


* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

h1 {
  text-align: center;
  font-size: 40px;
  margin-bottom: 30px;
}
.inter {
  font-family: "Inter", sans-serif;
  font-weight: 700;
  color: white;
}
.container {
  max-width: 730px;
  margin: 30px auto;
  min-width: 440px;
  overflow: auto;
  min-height: 670px;
  border: 1px solid #afbdb3;
  padding-top: 30px;
  padding-left: 30px;
  padding-right: 30px;
  padding-bottom: 30px;
  border-radius: 5px;
  margin-bottom: 70px;

}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>