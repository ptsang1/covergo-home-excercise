<script>
import PATHS from "../Routes/paths";
export default {
  methods: {
    onClick() {
      window.location.pathname = PATHS.PAGE_1;
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="content">
      <h1 class="header">Ooops</h1>
      <p>Your age is over our accepted limit.</p>
      <p>We are sorry but we can not insure you now</p>
      <button class="button" @click="onClick">Ok :(</button>
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
  margin-bottom: 20px;
}
.button {
  margin-top: 25px;
  background-color: #000;
  width: 200px;
  padding: 10px 0;
  color: #fff;
  border-radius: 6px;
  border-width: 0;
}
</style>
