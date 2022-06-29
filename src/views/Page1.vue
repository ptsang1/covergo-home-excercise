<script>
import PATHS from "../Routes/paths";
export default {
  methods: {
    onClick() {
      window.location.pathname = PATHS.PAGE_2;
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="content">
      <h1 class="header">Hello There!</h1>
      <p>Let's buy some insurance. It is going to take only a few steps</p>
      <button class="button" @click="onClick">Start</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  padding-top: 15vh;
  display: flex;
  justify-content: center;
}
.content {
  width: 80%;
  max-width: 800px;
  min-width: 280px;
  background-color: #eee;
  text-align: center;
  padding: 100px 20px;
}
.header {
  font-weight: bold;
  margin-bottom: 50px;
}
.button {
  margin-top: 25px;
  background-color: #000;
  width: 150px;
  padding: 10px 0;
  color: #fff;
  border-radius: 6px;
  border-width: 0;
}
</style>
