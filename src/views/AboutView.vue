<template>
  <div class="containerabout">
    <h1>This is an about page</h1>
    <div class="border-bottom"></div>
    <p>Welcome to our task list site, where organization meets efficiency in the digital age. We understand the complexities of modern life and the myriad of tasks that come with it. That's why we've designed a platform that seamlessly integrates into your daily routine, empowering you to stay on top of your tasks with ease. Whether you're managing personal projects, coordinating team assignments, or simply jotting down your daily to-dos, our intuitive interface ensures that nothing slips through the cracks. With customizable features tailored to your unique workflow, you can prioritize tasks, set deadlines, and track progress effortlessly. Say goodbye to scattered notes and forgotten appointments - our task list site is your one-stop solution for streamlined productivity. Join us today and experience the simplicity of staying organized in a chaotic world.</p>
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