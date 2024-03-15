<template>
  <div class="containerabout">
    <h1>404 Not Found</h1>
    <div class="border-bottom"></div>
    <p>Oops! It seems like you've taken a wrong turn.

The page you're looking for seems to have vanished into the digital ether. But don't worry, it's not lost forever. Our team of tech-savvy wizards is on the case, trying to summon it back from the depths of cyberspace.

In the meantime, why not explore some of our other pages? We've got plenty of interesting content just waiting to be discovered. Or, if you're feeling adventurous, you can always try your luck with another search.

And hey, if you think there's been a mistake or you need some assistance, feel free to reach out to our support team. They're experts at navigating the tangled web of the internet and are always happy to help.

Thanks for your patience, and happy browsing!</p>
    <div class="border-bottom"></div>
    <router-link class="backHome" to="/">Back to Homepage</router-link>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@700&display=swap");


* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
.backHome {
  font-size: 17px;

}

body {
  font-family: 'Poppins', sans-serif;
}
h1 {
  color: whitesmoke;
  font-family: "Lato", sans-serif;
  font-weight: 700;}

.border-bottom {
    border-bottom: 1px solid #ccc;
    margin-top: 15px;
    margin-bottom: 15px;
}

.containerabout {
  max-width: 730px;
  margin: 30px auto;
  overflow: auto;
  min-height: 500px;
  border: 1px solid #afbdb3;
  padding: 30px;
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