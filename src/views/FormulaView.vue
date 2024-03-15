<template>
  <div class="container">
    <ListFootballEvents />
  </div>
</template>

<script>
import ListFootballEvents from '@/components/ListFormulaEvents.vue'

export default {
  name: 'FootballView',
  props: [],
  data() {
    return {
  
    };
  },
  components: {
    ListFootballEvents
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  margin: 30px auto;
  min-width: 670px;
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
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 99;
}
</style>