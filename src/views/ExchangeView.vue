<template>
  <div class="container">
    <ExchangeRate />
    <ExchangeRate />
  </div>
</template>

<script>
import ExchangeRate from '@/components/ExchangeRate.vue';


export default {
  name: 'ExchangeView',
  components: {
    ExchangeRate
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
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